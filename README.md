### Create 2018年5月30日
# EFOS3.0
为了能适应未来的开发方式，充分利用现有技术来提高开发效率和平台的稳定性。由于现有功能代码也有不小的数量级，重新推翻重写语法和逻辑工作量太过庞大，所以新框架需要能兼容现有语法和新的语法，然后渐进式的逐步淘汰。
## 技术栈
- **[webpack](#webpack)**
- **[react](#react) （94kb）**
- **[babel](#babel) （88kb）**
- **[axios](#axios) （13kb）**
- **[director](#director)（10kb）**
- **[handlebars](#handlebars)（20kb）**
- **[sass](#sass)**
- **[jQuery](#jquery) （94kb）**
- **[highcharts](#highcharts)**
- **[datatables](#datatables)**
- **[font-awesome](#font-awesome)**
- **[bootstrap](#bootstrap)**
### 分析
### webpack
- 模块化打包，支持ES6，AMD，CMD，Commonjs等模块方式
- 开发模式下的文件监听，热更新，热加载，相比之前速度很大提升
- 使用loader加载器完成各种开发语言的预编译
- 代码分离，按需加载js和css
- 生产模式下代码/静态文件压缩，路径指定，功能模块分离
- 可配置使用很多功能强大的插件和加载器等，扩展性强
### react
- 使用jsx语法开发，js内嵌模版
- 虚拟DOM，组件化开发，组件化生命钩子
- MVVM框架，数据视图双向绑定
### babel
- 支持ES6语法，如promise，class，Array.prototype.include等
### axios
- ajax的promise封装
- 写法简单，可向后台发送数据前后打断并进行统一处理
- 防止客户端XSRF攻击
### director
- 简单、易用、小巧的hash路由
### handlebars
- template模版语法，嵌入数据，并且可以进行简单的逻辑处理
- 与React等MVVM框架用法有冲突，为了能支持之前的写法，先保留
### sass
- css另一种语法，可提高开发效率
- 提供变量，嵌套，混合，通过函数进行颜色值与属性值的运算等强大功能
### jQuery
- js方法库，提供大量简单，易用的DOM处理方法
### highcharts
- 数据可视化插件，支持柱状图，饼图，曲线，地图等许多复杂图形
### datatables
- 表格插件，支持表头固定，自定义渲染，列固定，表格事件处理等强大功能，依赖jquery(有点顾虑，但是没办法)
### font-awesome
- 字体矢量图片，通过设置字体样式可自定义图片的大小和颜色
### bootstrap
- 提供很多自适应的控件库，如弹框，滚播，提示框等等，后期可能更换为react-bootstrap

## 新旧框架对比
- 开发模式下文件监听只对修改部分打包，时间从6s减少至2s左右
- 开发模式下热加载时，样式修改不需要刷新浏览器即呈现效果，且功能性代码修改后重新加载时间较之前快很多，减少等待时间，提高开发效率
- 生产打包后文件层次最多2层，相比之前9层，找文件方便很多，开发模式下文件层次也较之前少
- 生产打包进行压缩，通用代码抽离，模块分离，CDN等使发布文件体积较之前减少很多
- 路由相对之前更简单，易懂，稳定性强，路由时刻与功能模块--对应，且新增404界面，统一由路由匹配，匹配不到则404
- jsx和ES6语法相比之前的jquery的DOM操作稳定性更强，提升界面响应，书写简洁等，sass语法提供变量，嵌套，混合，通过函数进行颜色值与属性值的运算等强大功能，可统一管理主题颜色代码等，提升开发效率
- 可扩展巨量、实用、强大的功能，如autoprefixer（还未添加进框架中的功能），自动化处理代码，减少代码书写量
- 使用数量级大，遇到问题网络上较容易查找，之前的框架scrat基本处于停止维护更新的状态，且使用的人很少
## 文件目录
- **|—— dist** （发布文件，build生产后才会存在）
- **|—— src**  （开发文件）
     - **|—— common** （行业通用代码）
          - **|—— treelist** （左侧功能导航栏）
          - **|—— footer** （底部）
          - **|—— header** （头部导航栏）
          - **|—— NotFind** （404界面）
          - **|—— theme** （主题）
          - **|—— summaryInfo** （集团/实时监控右侧面板）
          - **|—— components** （功能文件）
               - **|——** （. . .其他开发的功能模块）
     - **|—— community**（ 物业）
          - **|—— group** （集团入口）
               - **|——** （. . .其他开发的功能模块）
          - **|—— project** （物业项目入口）
               - **|——** （. . .其他开发的功能模块）
     - **|—— industry** （工业）
          - **|—— project** （工业项目入口）
               - **|——** （. . .其他开发的功能模块）
     - **|—— plugins** （插件）
     - **|—— static** （静态）
          - **|—— share** （通用图片）
     - **|—— http.js** （请求发送和接收统一处理）
     - **|—— index.scss** （行业通用样式）
     - **|—— url.js** （功能点与文件路径匹配配置）
     - **|—— router.js** （路由统一处理）
     - **|—— iGroup.html** （集团入口模版（多入口））
     - **|—— iProject.html** （项目入口模版（多入口））
     - **|—— iGroup.js** （集团入口（多入口））
     - **|—— iProject.js** （项目入口（多入口））
     - **|—— index.html** （应用平台入口模版（单入口））
     - **|—— index.js** （应用平台入口（单入口））
- **|—— package.json** （依赖包描述）
- **|—— README.md** （框架介绍）
- **|—— server.js** （本地node服务器）
- **|—— webpack.config.js** （webpack开发配置）
- **|—— webpack.prod.js** （webpack生产配置）

- ### CDN （减少打包时间和发布文件的体积）
  - **|—— lib.js** （静态js插件库）
  - **|—— jquery.ui.css** (时间控件样式)
  - **|—— bootstrap.min.css** （bootstrap样式）
  - **|—— jquery.datatables.css** （datatable样式）
  - **|—— font-awesome.min.css** （字体图片样式）

PS:行业之间有重复代码，按照现在的界面风格完全可以去掉group和project层减来少文件体积，保留group和project层是为了满足以后可能各行业之间的集团和项目界面都不一致的情况。
## 集团入口
```es6
import './index.scss';
import React, { Component } from 'react';
import ReactDOM from 'react-dom';
import Group from 'community/group/group.js';
import Theme from 'common/theme/theme';
import './http'
const theme = new Theme();

//全局store仓库
window.EFOS_STORE = {};
// 渲染页面骨架
ReactDOM.render(<Group theme={theme}/>, document.getElementById('efos-root'))
//主题加载
theme.init();

if (process.env.NODE_ENV === 'development') {
   if (module.hot) {
      module.hot.accept();
   }
}
```
## 项目入口
```es6
import './index.scss';
import React from 'react';
import ReactDOM from 'react-dom';
import Theme from 'common/theme/theme';
import './http'
const theme = new Theme();

//行业判定
const relation = {
   community: () => import(/* webpackChunkName: "community"*/ "community/project/project.js"),
   industry: () => import(/* webpackChunkName: "industry"*/ "industry/project/project.js")
}[location.pathname.split('/')[1]];

relation().then((Project) => {
   //全局store仓库
   window.EFOS_STORE = {};
   // 渲染页面骨架
   ReactDOM.render(<Project.default theme={theme} />, document.getElementById('efos-root'))
   //主题加载
   theme.init();
}).catch((err) => {
   console.error(err)
 })

if (process.env.NODE_ENV === 'development') {
   if (module.hot) {
      module.hot.accept();
   }
}
```
## CLI
环境安装：`$ npm install -g`
开发模式下：`$ npm run server`
生产模式下：`$ npm run build`
## 开发软件
`Visual Studio Code`
`webstorm`
`sublime text`

建议使用 `Visual Studio Code`，功能扩展性强，界面友好，代码调试，集成终端
## 涉及的语法
- jsx
- ES6/ES5
- jquery
- sass
## 浏览器兼容性
1. **FireFox**
2. **Chrome**
3. **Opera**
4. **IE >= 10**
5. **360浏览器（极速模式和兼容模式IE>=10内核，最近版本默认IE11内核）**
6. **QQ浏览器（极速模式和兼容模式IE>=10内核，最近版本默认IE11内核）**
## 开发注意事项和建议
- 在编写代码时注意格式规范，多写注释
- 新的功能开发强烈建议用[React](https://www.reactjscn.com/)进行组件化开发，逐步向[React](https://www.reactjscn.com/)框架靠拢，抛弃jquery的DOM操作，提升界面响应
- 静态文件，即长期不需要改动的文件（js/css）先期通过CDN的方式引用，减少打包时间和文件体积，提升开发效率，后期建议将图片文件也通过CDN的方式引用，进一步提升打包效率
- 为了禁止各功能模块的样式冲突，应在组件被卸载时通过style-loader的unuse/unref删除样式
- 接口调用获取数据时，请使用Axios（不需要import，直接使用），方便对后台请求进行统一处理
- 通用的样式和模块，能提取出来就提取出来，放在通用文件中，并做好注释
- 通用模块的插件编写完成后，放入src/plugins/文件中，提供给其他功能调用
- 陆续将黑色样式提取出来放入blackTheme.useable.scss中
- 样式代码放在scss/css文件中，在js中import，之前的内嵌样式需要提取到样式文件中
- 下次发布的内容，在发布版本上开发、提交和修改，否则在开发版本上开发，且下次发布之前不能提交不需要发布的代码
## 未完成内容
- H5界面的路由路径和入口确定
- 框架环境安装测试
## 已完成主要内容
- 开发模式下的文件监听，热更新，热加载，自动打开浏览器键入网址，样式无刷新加载
- 生产模式下的文件打包优化，如css/js压缩、功能模块分离等
- 兼容旧的功能模块和最新的语法
- 路由监听并加载对应功能文件
- 各技术栈文件压缩后的大小测试
- 使用React重构了通用功能模块（header/foot/group/project等）和集团/项目入口代码
- http请求统一处理（参数处理，http路径修改，报错处理，请求头处理）
- 集团和项目样式分离，行业样式分离
- 项目界面入口行业分离
- 浏览器兼容性测试
- 开发环境下样式以style标签内嵌方式动态插入和生成环境下生成css文件link插入
- 不使用单个入口打包，多入口打包可方便兼容多行业扩展，样式代码分离等
- 路由加载功能时和该用户的权限功能进行对比，对比不成功则路由到404 NotFind
## 后续内容
- 创建新的svn开发地址
- notFind界面
- 按照PC样式规范重构PC前端样式代码
- 其他功能模块还没适应新框架，需要在移入时做些小修改
- 功能和通用样式分离，主题颜色和布局样式分离
- 深度优化打包时间和文件体积
- 重写老的功能代码，逐步淘汰handlebars
- 其他语法的扩展
- 自动化测试工具
## 总结
下周可以开始将大批量的功能模块稍加修改移入到新框架内，进行试用，并开始着手进行后续内容
