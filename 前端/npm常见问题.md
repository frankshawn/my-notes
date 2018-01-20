### 参考链接：
[阮一峰--npm模块管理器](http://javascript.ruanyifeng.com/nodejs/npm.html)

### npm install 下载缓慢？
> * 方法1、`npm config set registry https://registry.npm.taobao.org`
> * 方法2、使用 cnpm 替代 npm，请查看：[https://npm.taobao.org/](https://npm.taobao.org/)

### 依赖包在不同环境下一致性的问题
> * 方法1、npm shrinkwrap (用了 shrinkwrap 之后，仍有可能出现问题，尤其是在服务器使用 ci 自动构建时，因为最好在本地充分测试通过之后再提交到服务器)
> * 方法2、使用 yarn 替代 npm
