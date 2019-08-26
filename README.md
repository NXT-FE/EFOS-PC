### Created 2018年06月08日
### Updated 2019年08月22日 
## 技术栈
- **[webpack](#webpack)**
- **[react](#react) （94kb）**
- **[react-router](#react-router)**
- **[dva](#dva)**
- **[babel](#babel) （88kb）**
- **[axios](#axios) （13kb）**
- **[loadsh](#loadsh)**
- **[sass](#sass)**
- **[echarts](#echarts)**
- **[antd](#antd)**

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
### [react-router](https://www.npmjs.com/package/react-router)
- 基于react框架的路由
### [dva](https://dvajs.com/)
- 基于 redux 和 redux-saga 的数据流方案
- 全局状态管理，hook
- 能帮助react组件实现互通
- 逻辑和状态与UI分离，结构更清晰，后期维护定向修改方便
### [babel](https://babeljs.io/docs/en/)
- 支持下一代语法，如Promise，class，Array.prototype.include，模版字符串，箭头函数，解构，默认参数，扩展运算，迭代器，新的内嵌功能库等
- 打包编译ES6+=>ES5
- 提供各种plugins扩展语法，提升开发效率
### [axios](https://www.npmjs.com/package/axios/v/0.18.0)
- ajax的promise封装
- 写法简单，可向后台发送数据前后打断并进行统一处理
- 防止客户端XSRF攻击
### [loadsh](https://lodash.com/docs/4.17.11)
- 提供大量简单易用高效的函数，提升开发效率
### [sass](https://www.sasscss.com/)
- css另一种语法，可提高开发效率
- 提供变量，嵌套，混合，通过函数进行颜色值与属性值的运算等强大功能
### [echarts](https://echarts.baidu.com)
- 基于canvas技术的数据图形化插件
### [antd](https://ant.design/index-cn)
- 组件库，组件种类多，UI设计合理，提高开发效率

## 新旧框架
- 旧版本，通用度低，沉余代码，样式混乱，代码和命名不规范，开发过程中容易出现互相覆盖，BUG多
- 开发模式下文件监听只对修改部分打包，打包时间减少
- 开发模式下热加载时，样式修改不需要刷新浏览器即呈现效果，且功能性代码修改后重新加载时间较之前快很多，减少等待时间，提高开发效率
- 生产打包后文件层次最多2层，相比之前9层，找文件方便很多，开发模式下文件层次也较之前少
- 生产打包进行压缩，通用代码抽离，模块分离，CDN等使发布文件体积较之前少
- 路由相对之前更简单，易懂，稳定性强，路由时刻与功能模块--对应，统一由路由匹配，匹配不到则404
- jsx和ES6语法相比之前的jquery的DOM操作稳定性更强，提升界面响应，书写简洁等，sass语法提供变量，嵌套，混合，通过函数进行颜色值与属性值的运算等强大功能，可统一管理主题颜色代码等，提升开发效率
- 可扩展巨量、实用、强大的功能和语法编译，提升开发效率
- 使用数量级大，遇到问题网络上较容易查找，之前的框架scrat基本处于停止维护更新的状态，且使用的人很少

## 界面配置化
同一类组件可能存在多种样式/事件/接口参数/接口/，模版样式也是如此，如果一律通过配置生成界面，需要配置的数据太繁杂、耦合度太高，同级组件之间传递数据困难，维护困难，配置也麻烦
- 初步结论
   - 配置型界面只适合简单界面，没有太多逻辑复杂的事件和样式等，大部分还是通过功能js渲染界面（非配置型界面）
   - 通过配置生成界面是为了提高开发效率，非配置型界面也可以通过建立组件库+模版库的方式达到目的，开发功能js也会很快，只需要写简单的事件和逻辑即可，后期主要工作主要维护模版库和组件库
- 建议
   - 共存2种功能点渲染方式，一是通过place渲染配置型界面，二是通过功能js渲染对应界面（非配置型界面）
   
## 文件目录
- **|—— dist** （发布库）
    - **|—— 0.1.0**
    - **|—— 0.1.1**
    - **|—— x.x.x**（版本号，可在CLI中修改EFOS的版本号）
- **|—— src**  （开发库）
   - **|—— EFOS**（平台库）
      - **|—— template** （模版共享库）
      - **|—— component** （组件共享库）
      - **|—— interface** （非配置型界面渲染库）
      - **|—— H5** （H5界面库）
      - **|—— library**（ 功能性库 ）
            - **|—— components.js** （组件配置）
            - **|—— templates.js** （模版配置）
            - **|—— interface.js** （非配置型界面配置）
            - **|—— http.js** （接口统一处理）
            - **|—— place.js** （配置型界面模版组件位置处理）
            - **|—— router.js** （路由统一处理，请求interface对应关系或者place进行相应界面渲染）
            - **|—— H5.js** （对外H5界面统一渲染判定处理）
            - **|—— library.js** （功能性共享库，对外提供各种方法调用）
            - **|—— Loader.js** （全局文件异步加载错误提示，延时等统一处理）
            - **|—— ServerResourceGetter.js** （服务器CDN获取统一处理）
      - **|—— static** （静态库（图片，视频，音频等静态文件））
      - **|—— style** （非主题样式库）
      - **|—— theme** （主题库）
      - **|—— EFOS.js** （初始化全局数据存储_store和数据接口服务_api）
      - **|—— App.js** （主程序骨架）
      - **|—— App.model.js** （主程序模型文件）
      - **|—— antd-cover.scss** （覆盖antd样式文件）
      - **|—— index.scss** （通用样式）
      - **|—— index.html** （入口模版）
      - **|—— index.js** （入口控制）
      - **|—— login.scss** （登录样式）
      - **|—— login.html** （登录模版）
      - **|—— login.js** （登录控制）
      - **|—— login.model.js** （登录模型文件）
      - **|—— service.json** （数据接口服务配置文件）
- **|—— .eslintrc.json** （eslint配置文件）
- **|—— .browserslistrc** （autoprefixer样式规则）
- **|—— .babelrc** （babel配置文件）
- **|—— checkout.xml** （测试输出报告xml）
- **|—— package.json** （依赖包描述）
- **|—— README.md** （框架介绍）
- **|—— getApiConfig.js** （获取service.json配置的服务）
- **|—— server.js** （node开发、热更新服务）
- **|—— build.js** （构建服务）
- **|—— tsconfig.json** （TypeScript语法配置文件）
- **|—— webpack.common.js** （webpack通用）
- **|—— webpack.plat.js** （webpack平台配置）
- **|—— webpack.dev.js** （webpack开发，集成了eslint代码语法检测）
- **|—— webpack.prod.js** （webpack生产，集成了eslint代码语法检测）

## CLI
环境安装：`$ c?npm install`，后面有时间提供github下载

开发模式：`$ c?npm run server [args1] [args2]`
   - args1:平台名称（可传值：efos | nxt）（默认efos）
   - args2:监听端口号（默认3000，可在package.json中修改默认端口号port，修改该值可同时进行多平台热更新开发）

生产模式：`$ c?npm run build [args1] [args2]`
   - args1:平台名称（可传值：efos | nxt）（默认efos）
   - args2:版本号（打包后代码路径dist/args2）（默认0.1.0,可在package.json中修改默认版本version）

## 开发软件
`Visual Studio Code`
`webstorm`
`sublime text`

建议使用 `Visual Studio Code`，功能扩展性强，界面友好，代码调试，集成终端

## 语法支持
- jsx
- ES6/ES7
- sass
- TypeScript
## 内部全局变量（避免手动导入，提高开发效率）
- **React/ReactDOM**

   `建议使用rwwd快捷命令生成组件基本结构`
- **_app**

   `注册组件模型`  
   ``` es6
   _app.model({namespace,reducers,state,effects,subscriptions})
   ``` 
   详情看[dva](https://dvajs.com/)
- **_connect**

   `链接组件和redux`  
   ``` es6
   //返回的state会传到Example组件的this.props中，state中包含所有模型的state，可组件之间互通数据
   //第一种写法
   @_connect((state)=>state) 
   class Example extend Component{}
   //第二种写法
   export default _connect((state)=>state)(Example)
   ``` 
   - **_umas**

   `自动卸载model和style`  
   ``` es6
   //返回的state会传到Example组件的this.props中，state中包含所有模型的state，可组件之间互通数据
   //第一种写法
   @_connect((state)=>state) 
   @_umas({model,style})
   class Example extend Component{}
   ```
- **_api**

   `http请求路径`  
   ```es6
   _api[serviceCode][apiCode]
   ```
- **_store**

   `全局存放数据的对象，可通过该对象在不相关组件中互通数据,初始为{ Ver: '1.0', defaultServiceCode: 1 }`
- **Axios $post $get**

   `用于发起后台请求`  
   ``` es6
   $post(apiCode, parames, config = {}, serviceCode = 1).then(({data})=>{})
   $get(url,config={}).then(({data})=>{})
   //不建议使用这种
   Axios.post(url,params,config)
   ```
- **Promise**

   `承若，异步操作`
- **moment**

   `moment全局对象`
- **Loader**

   `用于按需异步请求加载组件/模版/非配置型界面等`  
   ``` es6
   const Example = Loader(()=>import(/*webpackChunkName:"example"*/ "component/example"))
   return <Example {...props}/>
   ```
- **Components**

   `组件ReactNode` 
   ``` es6
   const TableWrapper = Loader(Components.TableWrapper)
   ```
- **Templates**

   `模版ReactNode` 
   ``` es6
   const SingleDiv = Loader(Templates.SingleDiv)
   ```
- **Interface**

   `界面ReactNode` 
   ``` es6
   const blocManage = Loader(Interface.blocManage)
   ```
- **Library**

   `功能函数库`
   ``` es6
   const { DeepMerge } = Library
   ```
- **CodeName**

   `前端定义的code和name对应表和固定下拉数据`
   ``` es6
   const { OfflineReason } = CodeName;OfflineReason(code)||OfflineReason.Data({type,all,allId,allName})
   ``` 
   
## 文件类型支持（后续根据需要增加更多类型的编译支持）  
`.js` `.jsx` `.mjs` `.ts` `.tsx` `.scss` `.css` `.json` `.jpg` `.jpeg` `.png` `.bmp` `.gif` `.svg` `.xml` `.html` `.handlebars(不应被使用)`
## 原理
**加载关系图：**
![Image text](https://github.com/NXT-FE/EFOS-PC/blob/master/relation.jpg?v=2018101501)
**生成配置型界面数据结构：**
``` es6
let config = {
   template: 'template_9',
   components: {
      A: ['component_1',{...props}]
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

使用ESLint工具进行代码风格测试
开发完成后必须通过ESLint代码规范检测工具（检测规则待讨论）
## 版本控制
- 分为主库和分支，在分支上开发，提交必须携带日志，日志为相关文件解释说明，不同功能分开提交，方便写日志，不然太混乱
- 需要内测时将分支上代码合并到主库，执行打包发布到预发布平台
- 测试通过，选择性提交相关代码到主库
（git正在部署中...）
## 发布
1.手动打包请看[CLI](#CLI),然后通过ftp  192.168.1.31 进行传输，建议用下面的方式发布
2.jenkins发布 ，登录192.168.1.244:8080  hj/hjmima，选择对应发布任务进行一键构建发布，返回success为绿色则成功

## 兼容性
   1. **FireFox**
   2. **Chrome**
   3. **Opera**
   4. **IE >= 10**
   5. **360浏览器（极速模式和兼容模式IE>=10内核，最近版本默认IE11内核）**
   6. **QQ浏览器（极速模式和兼容模式IE>=10内核，最近版本默认IE11内核）**

## 开发注意事项和建议
- 在编写代码时注意格式规范，多写注释
- 根据需求，先期在antd上对比是否存在可使用组件，不存在则进行开发
- 编写组件或者模版时，在component或者template下建立文件夹将组件的功能和样式（不是必须）文件放入，
   编写属性匹配文件（xxx.d.ts），且完善components.js/templates.js中的配置信息           
- 使用[React](https://www.reactjscn.com/)进行组件化开发
- 通用的样式和模块，能提取出来就提取出来，放在通用文件index.scss
- 通用模块的方法或者插件编写完成后，放入src/library/library文件中，提供给其他功能调用
- 可使用Components,Templates全局变量快速引用组件/模版，如const FormWrapper =Loader(Components.FormWrapper);<FormWrapper/>
- 配置型渲染的数据json暂时先放在library/config.js中并导出，非配置型渲染文件放在interface中，并完善interface.js中的配置信息
- 由isPlace（boolean）判断该功能界面是否通过配置型渲染（true）
- 需要覆盖antd自带的样式放在antd-cover.scss中
- 需要手动重定向当前页面路由，可以使用全局_store.history对象，也可以通过redux中efos.history获取到，参考https://www.npmjs.com/package/history
- 获取接口路径方式：_api[服务id][接口id]
- 界面自适应按2个区间写媒介查询(min-width:1610px)||(max-width:1610px)
- 计时器可使用组件<Interval {call,time,trigger}><YourComponent></Interval>
- static/_@server_resource/目录下的文件在build时不会打包进去，记得将文件通过ftp上传到服务器对应文件目录中
```es6
   let url = ServerResource.getter("_@server_resource/images/device/PC/default/301/err.png");
   <ServerResource url="_@server_resource/images/weather/3.url.svg" />
   import url from "_@server_resource/.../xxx.png"
   background-image:url("_@server_resource/.../xxx.png")
   //如果是想获取json，txt这种文件内容就这么写
   ServerResource.getterContent("_@server_resource/file/xxx.txt",data=>{debugger});
```
- 要尽量使用_app.model将state状态相关移出来到单独的文件YourComponent.model.js中，YourComponent应该只需要存在单纯的UI或者少部分逻辑，然后在你的YourComponent中用_connect把redux关联起来，进而可以读取到其他组件的信息，后期也方便维护，写法参考全局变量[_connect](#_connect)和[_app](#_app)
