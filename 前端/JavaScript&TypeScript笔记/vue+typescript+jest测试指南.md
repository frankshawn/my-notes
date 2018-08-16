## 安装依赖包
`yarn add -D jest@23.5.0 ts-jest@23.1.3 vue-jest@2.6.0 @vue/test-utils@1.0.0-beta.24 @types/jest@23.3.1 babel-preset-env@1.7.0 cross-env@5.1.1`

## 添加 jest 配置
在package.json中添加：
```
"jest": {
  "moduleFileExtensions": [
    "js",
    "vue",
    "ts"
  ],
  "transform": {
    "^.+\\.ts$": "ts-jest",
    "^.+\\.vue$": "vue-jest"
  },
  "testRegex": "(/__tests__/.*|\\.(test|spec))\\.(ts|tsx|js)$"
}
```

## 配置 babel
创建 `.babelrc`，添加如下代码：
```
{
  "env": {
    "test": {
      "presets": [
        "env"
      ]
    }
  }
}
```

添加运行配置：
```
"test:unit": "cross-env NODE_ENV=test jest"
```

示例代码：
[https://github.com/shawnwang5/vue-boilerplate](https://github.com/shawnwang5/vue-boilerplate)

参考资料：
[https://vue-test-utils.vuejs.org/guides/#using-with-typescript](https://vue-test-utils.vuejs.org/guides/#using-with-typescript)
