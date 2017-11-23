---
本篇安装依赖均使用 cnpm
----
### 安装依赖
`cnpm install --save-dev webpack`  
`cnpm install -g webpack`

### 执行打包操作
1. 新建 webpack.config.js
1. 写入如下内容：  
```
	const path = require('path')
	const fs = require('fs')

	const nodeModules = {}
	fs.readdirSync('node_modules')
	    .filter(function (x) {
	        return [ '.bin' ].indexOf(x) === -1
	    })
	    .forEach(function (mod) {
	        nodeModules[ mod ] = 'commonjs ' + mod
	    })

	module.exports = {
	    entry: './src/app.js',
	    output: {
	        filename: 'bundle.js',
	        path: path.resolve(__dirname, 'dist')
	    },
	    target: 'node',
	    externals: nodeModules
	}
```
1. 执行打包操作，工程根目录（package.json所在目录）执行如下命令：  
`webpack`或者 webpack --config webpack.config.js


### 丑化代码
1. 安装 babel 以使 webpack 支持 es6  
`cnpm install --save-dev babel-loader babel-core babel-preset-env`
2. 修改 webpack.config.js
```
	const path = require('path')
	const fs = require('fs')
	const webpack = require('webpack');

	const nodeModules = {}
	fs.readdirSync('node_modules')
	    .filter(function (x) {
	        return [ '.bin' ].indexOf(x) === -1
	    })
	    .forEach(function (mod) {
	        nodeModules[ mod ] = 'commonjs ' + mod
	    })

	module.exports = {
	    entry: './src/app.js',
	    output: {
	        filename: 'app.js',
	        path: path.resolve(__dirname, 'dist')
	    },
	    target: 'node',
	    externals: nodeModules,
	    plugins: [
	        new webpack.optimize.UglifyJsPlugin({
	            minimize: true,
	            sourceMap: false,
	            compress: {
	                warnings: false,
	                sequences: true,
	                dead_code: true,
	                conditionals: true,
	                booleans: true,
	                unused: true,
	                if_return: true,
	                join_vars: true,
	                drop_console: false
	            }
	        })
	    ],
	    resolve: {
	        extensions: ['.js', '.json'],
	        modules: [path.join(__dirname, 'src'), 'node_modules']
	    },
	    module: {
	        rules: [
	            { test: /\.js$/, exclude: /node_modules/, loader: "babel-loader" }
	        ]
	    }
	}
```

### 复制静态资源
`cnpm i -S copy-webpack-plugin`  
使用方法参照：[https://github.com/kevlened/copy-webpack-plugin](https://github.com/kevlened/copy-webpack-plugin)

### 删除目录
`cnpm i -S clean-webpack-plugin`  
使用方法参照：[https://github.com/johnagan/clean-webpack-plugin](https://github.com/johnagan/clean-webpack-plugin)
