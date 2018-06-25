### Create 2018年6月08日

## 技术栈
- **[webpack](#webpack)**
- **[react](#react) （94kb）**
- **[react-router](#react-router)**
- **[babel](#babel) （88kb）**
- **[axios](#axios) （13kb）**
- **[sass](#sass)**
- **[highcharts](#highcharts)**
- **[antd](#antd)**
--------
与第一版相比去掉了 **jquery** /**datatable** /**handlebars** /**director** /**font-awesome** /**bootstrap**
<br/>
增加了 **react-router** /**antd**

### 分析
### [webpack](https://webpack.js.org/)
- 模块化打包，支持ES6，AMD，CMD，Commonjs等模块方式
- 开发模式下的文件监听，热更新，热加载，相比之前速度很大提升
- 使用loader加载器完成各种开发语言的预编译
- 代码分离，按需加载js和css
- 生产模式下代码/静态文件压缩，路径指定，功能模块分离
- 可配置使用很多功能强大的插件和加载器等，扩展性强
### [react](https://www.reactjscn.com/)
- 使用jsx语法开发，js内嵌模版
- 虚拟DOM，组件化开发，组件化生命钩子
- MVVM框架，数据视图双向绑定
### react-router
- 基于react框架的路由
### babel
- 支持ES6语法，如promise，class，Array.prototype.include等
### axios
- ajax的promise封装
- 写法简单，可向后台发送数据前后打断并进行统一处理
- 防止客户端XSRF攻击
### [sass](https://www.sasscss.com/)
- css另一种语法，可提高开发效率
- 提供变量，嵌套，混合，通过函数进行颜色值与属性值的运算等强大功能
### [antd](https://ant.design/index-cn)
- 组件库，组件种类多，UI设计合理，提高开发效率

## 新旧框架
- 旧版本，通用度低，沉余代码，样式混乱，代码和命名不规范，开发过程中容易出现互相覆盖，BUG多
- 开发模式下文件监听只对修改部分打包，时间从6s减少至2s左右
- 开发模式下热加载时，样式修改不需要刷新浏览器即呈现效果，且功能性代码修改后重新加载时间较之前快很多，减少等待时间，提高开发效率
- 生产打包后文件层次最多2层，相比之前9层，找文件方便很多，开发模式下文件层次也较之前少
- 生产打包进行压缩，通用代码抽离，模块分离，CDN等使发布文件体积较之前减少很多
- 路由相对之前更简单，易懂，稳定性强，路由时刻与功能模块--对应，统一由路由匹配，匹配不到则404
- jsx和ES6语法相比之前的jquery的DOM操作稳定性更强，提升界面响应，书写简洁等，sass语法提供变量，嵌套，混合，通过函数进行颜色值与属性值的运算等强大功能，可统一管理主题颜色代码等，提升开发效率
- 可扩展巨量、实用、强大的功能
- 使用数量级大，遇到问题网络上较容易查找，之前的框架scrat基本处于停止维护更新的状态，且使用的人很少

## 文件目录
- **|—— dist** （发布库，build后存在）
- **|—— src**  （开发库）
     - **|—— component** （组件库）
     - **|—— interface**（ 功能性库 ）
          - **|—— components.js** （组件配置）
          - **|—— templates.js** （模版配置）
          - **|—— http.js** （接口统一处理）
          - **|—— place.js** （模版组件关系）
          - **|—— router.js** （路由统一处理）
     - **|—— static** （静态库）
     - **|—— style** （非主题库）
     - **|—— template** （模版库）
     - **|—— theme** （主题库）
     - **|—— App.js** （程序入口）
     - **|—— index.scss** （通用样式）
     - **|—— index.html** （入口模版（单入口））
     - **|—— index.js** （入口（单入口））
- **|—— .eslintrc.json** （测试json）
- **|—— checkout.xml** （测试输出报告xml）
- **|—— package.json** （依赖包描述）
- **|—— README.md** （框架介绍）
- **|—— server.js** （本地node服务器）
- **|—— webpack.common.js** （webpack通用）
- **|—— webpack.dev.js** （webpack开发）
- **|—— webpack.test.js** （webpack测试）
- **|—— webpack.prod.js** （webpack生产）

## CLI
环境安装：`$ npm install`
<br /> 
开发模式：`$ npm run server`（默认3000端口） 或者 `$ npm start`（默认8080端口），建议使用`$ npm run server`
<br /> 
测试模式：`$ npm test`
<br /> 
生产模式：`$ npm run build`

## 开发软件
`Visual Studio Code`
`webstorm`
`sublime text`
<br/>
建议使用 `Visual Studio Code`，功能扩展性强，界面友好，代码调试，集成终端

## 语法
- jsx
- ES6
- sass

## 原理
**加载关系图：**
<br /> 
![Image text](https://github.com/NXT-FE/EFOS-PC/blob/master/relation.jpg)
<br /> 
**大致数据结构：**
``` es6
let config = {
   template: 'template_9',
   components: {
      A: 'component_1',
      B: 'component_2',
      C: {
         template: 'template_1',
         components: {
            A: 'component_3',
            B: 'component_3'
         }
      },
      D: {
         template: 'template_9',
         components: {
            A: 'component_3',
            B: 'component_3',
            C: {
               template: 'template_1',
               components: {
                  A: 'component_1',
                  B: 'component_2'
               }
            },
            D: 'component_3'
         }
      }
   }
}
```
## 代码规范和测试工具
现在前端比较流行的代码风格测试工具有 **ESLint** 和 **JSHint**
- **JSHint**
   支持配置文件，方便使用，支持了一些常用类库，支持基本的ES6，不支持自定义规则、无法根据错误定位到对应的规则。
- **ESLint**
   默认规则里面包含了JSHint的规则，易于迁移，可配置为警告和错误两个等级，或者直接禁用掉，支持插件扩展，可以自定义规则，可以根据错误定位到对应的规则，支持ES6，支持React的JSX，缺点是需要进行一些自定义配置，执行速度上不如jslint和jshint。 

建议使用ESLint工具进行代码风格测试
开发完成后必须通过ESLint代码规范检测工具（检测规则待讨论）
## 版本控制（暂定）
- 检出2个文件夹，检出的svn路径一致，一个为开发版，一个为发布版
- 不能提交下次不需要发布的内容，保持svn上始终为需要发布的内容，如果为多人协作开发且为下次不需要发布的内容（情况较少），则通过其他交流工具发送，然后本地覆盖。
- 发布给到测试或者到外网则使用发布版

## 发布
运行在src文件层级运行命令npm run build。
打包完成后复制整个dist文件夹到发布SVN提交，提交时SVN执行脚本自动同步代码到各个平台。
当只修改小量文件时可以复制单个文件，直接进行上传并删除老文件；同时修改hash，清除浏览器对该文件的缓存。
但是如果修改时有新增，删除组件时，覆盖后还需要一些额外操作，如修改该组件中的ID,trunk

## 兼容性
   1. **FireFox**
   2. **Chrome**
   3. **Opera**
   4. **IE >= 10**
   5. **360浏览器（极速模式和兼容模式IE>=10内核，最近版本默认IE11内核）**
   6. **QQ浏览器（极速模式和兼容模式IE>=10内核，最近版本默认IE11内核）**

## 开发注意事项和建议
- 在编写代码时注意格式规范，多写注释
- 使用[React](https://www.reactjscn.com/)进行组件化开发
- 书写主题或者非主题样式时记得注释该样式所属于哪个组件，样式只能用class选择器且命名需要与组件名相同，最好能使用继承，把样式局部于该组件下，不影响其他组件且易查找修改
- 接口调用获取数据时，请使用Axios（不需要import，直接使用），方便对后台请求进行统一处理
- 通用的样式和模块，能提取出来就提取出来，放在通用文件index.scss中，并做好注释
- 通用模块的方法或者插件编写完成后，放入src/interface/文件中，提供给其他功能调用


