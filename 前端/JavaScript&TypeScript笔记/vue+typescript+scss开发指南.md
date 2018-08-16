### 使用 typescript

#### 环境准备
1. 安装 nodejs、yarn
1. 执行 `yarn global add vue-cli@3.0.0-beta.6`
1. 执行 `vue create typescript-in-vue`，从此处开始，可以全部选择默认选项完成创建
1. 执行 `yarn add -D @vue/cli-plugin-typescript`
1. 执行 `yarn add -D typescript@2.7.1`
1. 执行 `vue invoke typescript`
1. 执行 `yarn add vue-class-component`
1. 执行 `yarn add vue-property-decorator`

#### 代码修改
1. 应用根目录创建 tsconfig.json
1. 添加如下代码：
```json
{
      "compilerOptions": {
        "target": "es5",
        "strict": true,
        "module": "es2015",
        "moduleResolution": "node",
        "experimentalDecorators": true,
        "lib": [
          "es2016",
          "dom"
        ]
      }
}
```

#### 常见问题
1. error: Parsing error: Unexpected character '@'
> 1. 执行 `yarn add -D @vue/eslint-config-typescript`
> 1. 修改 package.json 中的 `eslintConfig` 配置，如下所示
  ```json
  {
      "eslintConfig": {
          "root": true,
          "extends": [
              "@vue/typescript",
              "plugin:vue/essential",
              "eslint:recommended"
          ]
      }
  }
  ```

1. error: 'Component' is defined but never used (no-unused-vars)
> 修改 package.json 中的 `eslintConfig` 配置，如下所示
  ```json
  {
      "eslintConfig": {
          "root": true,
          "rules": {
              "no-unused-vars": "off"
          },
          "extends": [
              "@vue/typescript",
              "plugin:vue/essential",
              "eslint:recommended"
          ]
      }
  }
  ```

1. error: 'xxx' is not defined (no-undef)
> 修改 package.json 中的 `eslintConfig` 配置，如下所示
  ```json
  {
      "eslintConfig": {
          "root": true,
          "rules": {
              "no-undef": "off"
          },
          "extends": [
              "@vue/typescript",
              "plugin:vue/essential",
              "eslint:recommended"
          ]
      }
  }
  ```

#### 参考资料
1. [vuex-class](https://github.com/ktsn/vuex-class/)
1. [vue-class-component](https://github.com/vuejs/vue-class-component)
1. [vue-property-decorator](https://github.com/kaorun343/vue-property-decorator)

### 使用 scss

#### 环境准备
1. 执行 `yarn add -D sass-loader`
1. 执行 `yarn add -D node-sass`

#### 代码修改
1. 对 style 标签设置 `lang="scss"`
