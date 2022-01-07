### Latest Updated 2020 年 04 月 20 日 @nxt-hj

## 技术栈

-   **[webpack](#webpack)**
-   **[react](#react) （94kb）**
-   **[react-router](#react-router)**
-   **[dva](#dva)**
-   **[babel](#babel) （88kb）**
-   **[axios](#axios) （13kb）**
-   **[loadsh](#loadsh)**
-   **[sass](#sass)**
-   **[echarts](#echarts)**
-   **[antd](#antd)**

### 分析

### [webpack](https://webpack.js.org/)

-   模块化打包，支持 ES6，AMD，CMD，Commonjs 等模块方式
-   开发模式下的文件监听，热更新，热加载，相比之前速度很大提升
-   使用 loader 加载器完成各种开发语言的预编译
-   代码分离，按需加载 js 和 css
-   生产模式下代码/静态文件压缩，路径指定，功能模块分离
-   可配置使用很多功能强大的插件和加载器等，扩展性强

### [react](https://www.reactjscn.com/)

-   使用 jsx 语法开发，js 内嵌模版
-   虚拟 DOM，组件化开发，组件化生命钩子
-   MVVM 框架，数据视图双向绑定

### [react-router](https://www.npmjs.com/package/react-router)

-   基于 react 框架的路由,界面与地址保持一致，有 3 种模式（hash/browser/memory），本框架使用 Html5 browser 路由

### [dva](https://dvajs.com/)

-   基于 redux 和 redux-saga 的数据流方案
-   全局状态管理，hook
-   能帮助 react 组件实现互通
-   逻辑和状态与 UI 分离，结构更清晰，后期维护定向修改方便

### [babel](https://babeljs.io/docs/en/)

-   支持下一代语法，如 Promise，class，Array.prototype.include，模版字符串，箭头函数，解构，默认参数，扩展运算，迭代器，新的内嵌功能库等
-   打包编译 ES6+=>ES5
-   提供各种 plugins 的扩展，支持一些特殊写法，提升开发效率

### [axios](https://www.npmjs.com/package/axios/v/0.18.0)

-   ajax 的 promise 封装
-   写法简单，可向后台发送数据前后打断并进行统一处理
-   防止客户端 XSRF 攻击

### [loadsh](https://lodash.com/docs/4.17.11)

-   提供大量简单易用高效的函数，提升开发效率

### [sass](https://www.sasscss.com/)

-   css 另一种语法，可提高开发效率
-   提供变量，嵌套，混合，通过函数进行颜色值与属性值的运算等强大功能

### [echarts](https://echarts.baidu.com)

-   基于 canvas 技术的数据图形化插件

### [antd](https://ant.design/index-cn)

-   组件库，组件种类多，UI 设计合理，提高开发效率

## 新旧框架

-   旧版本，通用度低，沉余代码，样式混乱，代码和命名不规范，开发过程中容易出现互相覆盖，BUG 多
-   开发模式下文件监听只对修改部分打包，打包时间减少
-   开发模式下热加载时，样式修改不需要刷新浏览器即呈现效果，且功能性代码修改后重新加载时间较之前快很多，减少等待时间，提高开发效率
-   生产打包后文件层次最多 2 层，相比之前 9 层，找文件方便很多，开发模式下文件层次也较之前少
-   生产打包进行压缩，通用代码抽离，模块分离，CDN 等使发布文件体积较之前少
-   路由相对之前更简单，易懂，稳定性强，路由时刻与功能模块--对应，统一由路由匹配，匹配不到则 404
-   jsx 和 ES6 语法相比之前的 jquery 的 DOM 操作稳定性更强，提升界面响应，书写简洁等，sass 语法提供变量，嵌套，混合，通过函数进行颜色值与属性值的运算等强大功能，可统一管理主题颜色代码等，提升开发效率
-   可扩展巨量、实用、强大的功能和语法编译，提升开发效率
-   使用数量级大，遇到问题网络上较容易查找，之前的框架 scrat 基本处于停止维护更新的状态，且使用的人很少

## 界面配置化

同一类组件可能存在多种样式/事件/接口参数/接口/，模版样式也是如此，如果一律通过配置生成界面，需要配置的数据太繁杂、耦合度太高，同级组件之间传递数据困难，维护困难，配置也麻烦

-   初步结论
    -   配置型界面只适合简单界面，没有太多逻辑复杂的事件和样式等，大部分还是通过功能 js 渲染界面（非配置型界面）
    -   通过配置生成界面是为了提高开发效率，非配置型界面也可以通过建立组件库+模版库的方式达到目的，开发功能 js 也会很快，只需要写简单的事件和逻辑即可，后期主要工作主要维护模版库和组件库
-   建议
    -   共存 2 种功能点渲染方式，一是通过 place 渲染配置型界面，二是通过功能 js 渲染对应界面（非配置型界面）

## 文件目录

-   **|—— dist** （生产）
    -   **|—— 0.1.0**
    -   **|—— 0.1.1**
    -   **|—— x.x.x**（版本号，可在 CLI 中修改 EFOS 的版本号）
-   **|—— src** （开发）
    -   **|—— component**（组件）
    -   **|—— hook**（公共 hooK）
    -   **|—— library**（通用功能库，如 http 统一处理/通用函数/通用异步加载器/CDN 图片处理/全局引入/配置界面渲染处理/装饰器等）
    -   **|—— template**（模板）
    -   **|—— platform**（平台）
        -   **|—— UDS**（UDS 平台）
            -   **|—— interface** （非配置型界面）
            -   **|—— H5** （H5 库）
            -   **|—— navi** （导航）
            -   **|—— services** （公共接口服务）
            -   **|—— library**（ 平台功能 ）
                -   **|—— router.js** （路由统一处理，请求 interface 或者 place 进行界面渲染）
                -   **|—— H5.js** （H5 配置）
                -   **|—— config.js** （json 界面渲染配置）
                    ...
            -   **|—— static** （静态库（图片，视频，音频等静态文件））
            -   **|—— style** （非主题样式）
            -   **|—— theme** （主题）
            -   **|—— UDS.js** （平台相关全局引入）
            -   **|—— App.js** （主程序骨架）
            -   **|—— App.model.js** （主程序模型文件）
            -   **|—— antd-icons.js** （antd icon 定义文件，按需加载减少文件体积）
            -   **|—— antd-cover.scss** （覆盖 antd 样式文件）
            -   **|—— index.scss** （通用样式）
            -   **|—— index.html** （入口模版）
            -   **|—— index.js** （入口控制）
            -   **|—— login.scss** （登录样式）
            -   **|—— login.html** （登录模版）
            -   **|—— login.js** （登录控制）
            -   **|—— login.model.js** （登录模型文件）
            -   **|—— service.json** （数据接口服务配置文件）
        -   ...
        -   **|—— NXT**（接口文档平台）
            -   **与 EFOS 平台类似，在此不一一列出**
        -   **|—— MRO**（运维平台）
            -   **与 EFOS 平台类似，在此不一一列出**
    -   ...
-   **|—— .eslintrc.json** （eslint 配置）
-   **|—— .browserslistrc** （autoprefixer 样式规则）
-   **|—— .babelrc** （babel 配置）
-   **|—— checkout.xml** （测试输出报告 xml）
-   **|—— package.json** （依赖包描述）
-   **|—— README.md** （框架介绍）
-   **|—— getApiConfig.js** （获取 service.json 配置的服务）
-   **|—— server.js** （node 开发、热更新服务）
-   **|—— build.js** （构建服务）
-   **|—— cssr-loader.js**（webpack loader-本地和服务器文件构建控制）
-   **|—— dynamic-loader.js**（webpack loader-异步导入构建控制）
-   **|—— tsconfig.json** （TypeScript 语法配置文件）
-   **|—— webpack.common.js** （webpack 通用配置）
-   **|—— webpack.plat.js** （webpack 平台配置）
-   **|—— webpack.dev.js** （webpack 开发配置，集成了 eslint 代码语法检测）
-   **|—— webpack.prod.js** （webpack 生产配置，集成了 eslint 代码语法检测）
-   **|—— WebpackHtmlPrePlugin.js** （webpack plugin-依据平台和部署环境插入性能优化项）
-   **|—— webpackPreloadPlugin.js** （webpack plugin-构建分析）

## CLI

环境安装：`$ npm install`

获取接口文件：`$ npm run gs [args1] [args2]`

-   args1:环境（可传值：dev | test | rel | mrel | prod）（默认 dev）
-   args2:平台（可传值：uds | nxt | mro）（默认 uds）

开发模式：`$ npm run server [args1] [args2]`

-   args1:平台（可传值：uds | nxt | mro）（默认 uds）
-   args2:监听端口号（默认 3000，可在 package.json 中修改默认端口号 port，修改该值可同时进行多平台热更新开发）

生产模式：`$ npm run build [args1] [args2]`

-   args1:平台（可传值：uds | nxt | mro）（默认 uds）
-   args2:版本号（打包后代码路径 dist/args2）（默认 0.1.0,可在 package.json 中修改默认版本 version）

发布：`$ npm run publish [args1] [args2] [args3]`

-   args1:环境（可传值：dev | test | rel | mrel | prod）
-   args2:分支名称
-   args3:平台（可传值：uds | nxt | mro）（默认 uds）

## 开发软件

`Visual Studio Code`
`webstorm`
`sublime text`

建议使用 `Visual Studio Code`，功能扩展性强，界面友好，代码调试，集成终端

## 语法支持

-   jsx
-   ES6/ES7
-   sass
-   TypeScript

## 内部全局变量（避免手动导入，提高开发效率）

#### **React/ReactDOM**

`建议安装插件Reactjs code snippets，使用rwwd快捷命令快速生成react组件基本结构`

#### **Place**

`处理模板和组件嵌套关系的组件，请看这边`[加载关系图](#配置数据渲染)

```jsx
<Place {...config} />
```

#### **\_app**

`注册组件模型`

```es6
_app.model({ namespace, reducers, state, effects, subscriptions });
//全局发起state更新，重渲
_app._store.dispatch({ type, ...state });
```

详情看[dva](https://dvajs.com/)

#### **\_connect**

`链接组件和redux`

```es6
//返回的state会传到Example组件的this.props中，state中包含所有模型的state，可组件之间互通数据
//第一种写法
@_connect((state)=>state)
class Example extend Component{}
//第二种写法
export default _connect((state)=>state)(Example)
```

#### **\_umas**

`自动装载/卸载model和style，model何style都支持数组类型`

```es6
import style from "XXX.use(able)?.scss";
import model from "XXX.model(.js)?";
@_connect((state)=>state)
@_umas({model,style})
class Example extend Component{}
```

#### **\_api**

`http请求路径`

```es6
_api[apiCode];
```

#### **\_store**

`全局存放数据的对象，可通过该对象在组件中共享非组件状态数据，组件状态建议使用redux管理，初始为{ Ver: '1.0', defaultServiceCode: 1 }`

#### **Axios $post $get**

`用于发起后台请求`

```es6
$post(apiCode, parames, (config = {})).then(({ data }) => {});
$get(url, (config = {})).then(({ data }) => {});
//不建议使用这种
Axios.post(url, params, config);
```

#### **moment**

`moment全局对象`

#### **\_**

`lodash全局对象`

#### **Loader**

`用于按需异步请求加载组件/模版/非配置型界面等`

```es6
//组件
import { TableWrapper } from 'component'; //会在打包期间转成异步导入
const Example = Loader('component.ModalWrapper');
//模板
const LineHorizontal = Loader('template.LineHorizontal');
//界面
const trajectory = Loader('interface/trajectory');
//H5
const VideoPlay = Loader('H5/SituationVideo/VideoPlay/VideoPlay');
//其他,注意：('/A.B')--A代表文件名，B代表构建后文件名，B可省略，注意B的重复问题
const CCC_Video = Loader('interface/syntheticalSituation/Layout2/3C/video.CCC_Video');
```

#### **Library**

`功能函数库`

```es6
const { DeepMerge } = Library;
```

#### **CodeName**

`前端定义的code和name对应表和固定下拉数据`

```es6
const { OfflineReason } = CodeName;
OfflineReason(code) || OfflineReason.Data({ type, all, allId, allName });
```

#### **ServerResource**

`为了加快打包速度和文件体积，图片文件CDN获取，支持本地开发和打包时自适应切换来源`

```es6
let url = ServerResource.getter("_@server_resource/images/device/PC/default/301/err.png");
<ServerResource url="_@server_resource/images/weather/3.url.svg" />
import url from "_@server_resource/.../xxx.png"
background-image:url(~_@server_resource/.../xxx.png)
//如果是想获取json，txt这种文件内容就这么写
ServerResource.getterContent("_@server_resource/file/xxx.txt",data=>{debugger});
```

## 文件类型支持（后续根据需要增加更多类型的编译支持）

`.js` `.jsx` `.mjs` `.ts` `.tsx` `.scss` `.css` `.json` `.jpg` `.jpeg` `.png` `.bmp` `.gif` `.svg` `.xml` `.html` `.handlebars(不应被使用)`

## 配置数据渲染

**加载关系图**
![Image text](https://github.com/NXT-FE/EFOS-PC/blob/master/loadRelation.jpg)
**生成配置型界面数据结构：**

```es6
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

-   **JSHint**
    支持配置文件，方便使用，支持了一些常用类库，支持基本的 ES6，不支持自定义规则、无法根据错误定位到对应的规则。
-   **ESLint**
    默认规则里面包含了 JSHint 的规则，易于迁移，可配置为警告和错误两个等级，或者直接禁用掉，支持插件扩展，可以自定义规则，可以根据错误定位到对应的规则，支持 ES6，支持 React 的 JSX，缺点是需要进行一些自定义配置，执行速度上不如 jslint 和 jshint。

使用 ESLint 工具进行代码风格测试
开发完成后必须通过 ESLint 代码规范检测工具

## 版本控制

分支关系图基本如下
![Image text](https://github.com/NXT-FE/EFOS-PC/blob/master/gitVersion.png)

gitlab 上分支类型

-   BUG 分支：fix-发布时间-功能描述
-   功能分支：feat-发布时间-功能描述
-   测试分支：release-发布时间-描述
-   正式生产分支：master,tag
-   线上修复分支：hotfix-发布时间-描述
-   受保护分支：develop,master

注意事项

1. 已发布线上的不能再改，需要临时发布的建 hotfix 分支或者等后期项目一起发布
2. 内测前提交合并请求至 dev 分支，指派和通知其他人进行审核

### 提交日志格式

`<type>(<scope>): <subject>`

-   type
    修改类型

```es6
   interface type {
      fix:string//修复bug
      feat:string//新功能
      pro:string//优化
      doc:string//文档注释
   }
```

-   scope
    修改区域
-   subject
    修改描述

## 发布

-   项目开发完需要提交内测时，在 gitlab 发起 Merge Request 合并 feat 分支到 develop，组内人员相互审核，如果代码通过审核，则 merge，代码有问题或者可以优化的继续修改，直至可以 merge
-   内测分支和预发布分支全程由 web hook push event 管道 pipe 触发 jenkins 自动打包文件上传发布并反馈发布结果给到 gitlab，
    发布结果有 4 种状态 暂停/运行 running/sucess/error
-   正式环境由运维人员代理发布

## 兼容性

1. **FireFox**
2. **Chrome**
3. **Opera**
4. **IE >= 10**
5. **360 浏览器（极速模式和兼容模式 IE>=10 内核，最近版本默认 IE11 内核）**
6. **QQ 浏览器（极速模式和兼容模式 IE>=10 内核，最近版本默认 IE11 内核）**

## 开发注意事项和建议

-   在编写代码时注意格式规范，多写注释
-   根据需求，先期在 antd 上对比是否存在可使用组件，不存在则进行开发
-   通用的样式和模块，能提取出来就提取出来，放在通用文件 index.scss
-   配置型界面，使用渲染数据 json 通过[Place](#Place)实现
-   由 isPlace（boolean）判断该功能界面是否通过配置型渲染（true）
-   需要覆盖 antd 自带的样式放在 antd-cover.scss 中
-   需要手动重定向当前页面路由，可以使用全局\_store.history 对象，也可以通过 redux 中 efos.history 获取到，参考https://www.npmjs.com/package/history
-   因为会自动卸载样式,所以没有启用 css 编译时的 module 功能，类名不会添加 hash，但是开发时还是要养成习惯尽量在你的样式前加一层父级嵌套，减少样式冲突，相互影响的可能性，但是层级尽量不要太深
-   开发时建议使用[\_umas](#_umas)装饰器，可自动装载和卸载 model 和 style，减少重复性的工作，减少开发量
-   static/\_@server_resource/目录下的文件在 build 时不会打包进去，开发时 server_resource 文件路径指向局域网 34，记得将文件通过 ftp 上传到服务器对应文件目录中
-   要尽量使用\_app.model 将 state 状态相关移出来到单独的文件 YourComponent.model.js 中，YourComponent 应该只需要存在单纯的 UI 或者少部分逻辑，然后在你的 YourComponent 中用\_connect 把 redux 关联起来，进而可以读取到其他组件的信息，后期也方便维护，写法参考全局变量[\_connect](#_connect)和[\_app](#_app)
-   编写组件/模板时需要在 d.ts 文件中进行功能和参数说明
