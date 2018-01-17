# babel-plugin-transform-regenerator

>  异步转换 / 利用再生器进行再生 Transform async/generator functions with [regenerator](https://github.com/facebook/regenerator)

## 示例 

**In**

```javascript
function* a() {
  yield 1;
}
```

**Out**

```javascript
var _marked = [a].map(regeneratorRuntime.mark);

function a() {
  return regeneratorRuntime.wrap(function a$(_context) {
    while (1) {
      switch (_context.prev = _context.next) {
        case 0:
          _context.next = 2;
          return 1;

        case 2:
        case "end":
          return _context.stop();
      }
    }
  }, _marked[0], this);
}
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-regenerator
```

## 用法

### 通过 `.babelrc` (推荐)

无选项:

```json
{
  "plugins": ["transform-regenerator"]
}
```

设置选项:

|name|default value|
|---|---|
|asyncGenerators|true|
|generators|true|
|async|true|

```json
{
  "plugins": [
    ["transform-regenerator", {
      "asyncGenerators": false,
      "generators": false,
      "async": false
    }]
  ]
}
```

### 通过 CLI脚手架

```sh
babel --plugins transform-regenerator script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-regenerator"]
});
```
