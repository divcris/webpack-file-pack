# webpack-file-pack
webpack单文件多文件打包原理

看了许多篇文章，觉得这篇文章是让我受益最多的，故而引来留个笔记，方便自己查阅

## 单文件打包
```javascript
// src/single/index.js
var index2 = require('./index2');
var util = require('./util');
console.log(index2);
console.log(util);

// src/single/index2.js
var util = require('./util');
console.log(util);
module.exports = "index 2";

// src/single/util.js
module.exports = "Hello World";

// 通过 config/webpack.config.single.js 打包
const webpack = require('webpack');
const path = require('path')

module.exports = {
  entry: {
    index: [path.resolve(__dirname, '../src/single/index.js')],
  },
  output: {
    path: path.resolve(__dirname, '../dist'),
    filename: '[name].[chunkhash:8].js'
  },
}
```
index.js引入了的
