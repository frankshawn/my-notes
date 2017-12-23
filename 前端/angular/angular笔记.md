### 使用 sass 后，>>> 选择器无效?
> 使用 /deep/ 代替

### 私有属性只能在 @Component 所在的 class 内部访问，在 template 文件中不能访问私有属性

### Cannot find name 'require'
> 修改 tsconfig.app.json
> 增加：
```js
"types": [
  "node"
]
```
> 完整示例如下：
```js
{
  "extends": "../tsconfig.json",
  "compilerOptions": {
    "outDir": "../out-tsc/app",
    "module": "es2015",
    "baseUrl": "",
    "types": [
      "node"
    ]
  },
  "exclude": [
    "test.ts",
    "**/*.spec.ts"
  ]
}
```

### 在 webstorm 中无法识别 angular 的指令和属性？
> `routerLink` 之类的属性、`*ngIf` 之类的指令，默认情况下无法识别，提示"unknown tag not allow here"，此时需按照如下步骤解决问题：
>1. setting -- languages & frameworks -- javascript -- libraries -- download -- angular
>1. 下载 angular.js ，将其添加到工程所在的目录中

### 动态组件的开发
> 1. 若动态内容，在组件的内部不需要重复出现，可使用 ng-content
> 1. 若动态内容，在组件内部存在重复使用的情况，可使用 ngTemplateOutlet

### attr. 的使用场景
> 设置 HTML 标签特性使用 attr.attributeName，设置 DOM 特性时，直接使用属性绑定。

### 模板插值相关
#### 不能用的：
> 1. 带有 new 运算符的表达式
> 1. 赋值表达式
> 1. 带有 ; 或者 , 的链式表达式
> 1. 带有自增或者自减操作的表达式
> 1. 不支持位运算，| 在模板表达式中是管道
> 1. 模板表达式不能引用任何全局命名空间中的成员，比如：window、console
>
> *其中使用场景 1、2、3、4 是可能引发副作用的 javascript 表达式*

### Currency Pipe
> **语法格式：**
expression | currency[:currencyCode[:symbolDisplay[:digitInfo]]]
参数 currencyCode 表示要格式化的目标货币格式，其值为 ISO 4217 货币码，如：CNY 为人民币，
USD 为美元，EUR 为欧元等。
参数 symbolDisplay 表示以该类型为货币的哪种显示格式，其值为 Boolean 类型，true 表示
货币符号，如：$ 等，false 则表示显示 ISO 4217 货币码，如：CNY、USD 等。
参数 digitInfo 参照 DecimalPipe 管道中的格式说明。

### 关于管道
#### 纯管道
> 如果所转换的目标是对象，修改对象的内部属性，并不会执行 transform 函数。
#### 非纯管道
> angular 组件在每个变化周期都会监测并执行 transform 函数。

### 快速引用 node_modules 中的 css 文件
> 使用：`@import "~bootstrap/dist/css/bootstrap.css";` 相当于：`@import "../node_modules/bootstrap/dist/css/bootstrap.css";`，
"~" 前缀和 `node_modules` 的路径相等。详情[请点击](https://github.com/webpack-contrib/sass-loader#imports)链接查看。
