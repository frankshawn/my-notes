1. 在使用 Vue.component 注册组件时，data 必须是函数
1. 父组件的模板不应该知道子组件的状态
1. 在字符串模板中可以使用 kebab-case、camelCase、TitleCase，但是在HTML模板中应当始终使用 kebab-case，因为 HTML 模板受HTML的约束
1. 如果组件未经slot传递内容，可使用闭合的单标签，这种标签只能写在字符串模板中，因为自定义的标签是无效的HTML，浏览器的原生解析器无法识别它
1. 如果组件有 inline-template 属性，组件把它的内容当做模板，而不是分发内容
1. 在 script 标签中，设置 type="text/x-template" 并指定一个 id，可以将 id 直接指定给注册组件时的 template 属性，从而实现在 script 标签中配置模板
1. vue 实例在初始化时，对 data 的属性执行 getter/setter 的转化过程，因此属性必须在 data 对象上，vue 才能转化它
