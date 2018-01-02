## 闭包
> * 定义在函数内部的函数，可以访问其外部的变量、函数
> * 函数可以访问其所在词法环境的变量、函数

## for of 和 for in 的区别
> for in 遍历的是对象属性名、数组的键名；for of 可迭代对象定义的迭代值，调用的是可迭代对象的 iterator 函数。


## es6 函数非尾部默认值
```javascript
function f(x = 1, y) {
  return [x, y];
}

f() // [1, undefined]
f(2) // [2, undefined])
f(, 1) // 报错
f(undefined, 1) // [1, 1]
```
*这个问题应特别注意*


## 关于箭头函数
>1. 箭头函数不会创建自己的this，它使用封闭执行上下文环境的this值
>1. 不可以当作构造函数，也就是说，不可以使用new命令，否则会抛出一个错误
>1. 不可以使用arguments对象，该对象在函数体内不存在。如果要用，可以用 rest 参数代替
>1. 不可以使用yield命令，因此箭头函数不能用作 Generator 函数

## 关于严格模式
>1. 变量必须声明后再使用
>1. 函数的参数不能有同名属性，否则报错
>1. 不能使用with语句
>1. 不能对只读属性赋值，否则报错
>1. 不能使用前缀 0 表示八进制数，否则报错
>1. 不能删除不可删除的属性，否则报错
>1. 不能删除变量delete prop，会报错，只能删除属性delete global[prop]
>1. eval不会在它的外层作用域引入变量
>1. eval和arguments不能被重新赋值
>1. arguments不会自动反映函数参数的变化
>1. 不能使用arguments.callee
>1. 不能使用arguments.caller
>1. 禁止this指向全局对象
>1. 不能使用fn.caller和fn.arguments获取函数调用的堆栈
>1. 增加了保留字（比如protected、static和interface）

## ES6 模块与 CommonJS 模块的差异
>1. CommonJS 模块输出的是一个值的拷贝，ES6 模块输出的是值的引用
>1. CommonJS 模块是运行时加载，ES6 模块是编译时输出接口

## Error 对象
>1. Error: 通用 Error 对象，参考链接：[请点击](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error)
>1. EvalError: 执行全局的 eval 函数发生错误时的 Error 对象（还未纳入当前 es 版本中），参考链接：[请点击](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/EvalError)
>1. InternalError: js 执行引擎内部错误的 Error 对象（尚未未标准化），参考链接：[请点击](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/InternalError)
>1. RangeError: 数据值不在集合或者允许的值范围之内时的 Error 对象，参考链接：[请点击](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RangeError)
>1. ReferenceError: 使用某个变量时，如果该变量未定义时的 Error 对象，参考链接：[请点击](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ReferenceError)
>1. SyntaxError: js 引擎在对文件进行语法解析出现语法错误时的 Error 对象，参考链接：[请点击](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/SyntaxError)
>1. TypeError: 数据值不是期望的数据类型时的 Error 对象，参考链接：[请点击](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypeError)
>1. URIError: 全局的 URI 处理函数被错误地使用时的 Error 对象，参考链接：[请点击](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/URIError)
>
> 由于上述所述内容，截止到 2018/01/03，部分存在尚未标准化的问题(error 的类型、constructor 的入参等)，因此应避免使用未标准化的内容，以免造成语法错误。
