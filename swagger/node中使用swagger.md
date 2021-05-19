##### 安装 swagger-ui-express与swagger-jsdoc

```shell
npm install swagger-ui-express swagger-jsdoc@6.0.0 -S
```

##### 使用

新建 `./utils/swagger/index.js`文件

```js
// const path = require('path');
const express = require('express');
const swaggerUI = require('swagger-ui-express');
const swaggerDoc = require('swagger-jsdoc');
//配置swagger-jsdoc
const options = {
  swaggerDefinition: {
    openapi: '3.0.0',
    info: {
      title: 'api',
      version: '1.0.0',
      description: 'swagger-test',
    },
  },
  apis: ['./node_resource/node_router/*.js'],
};

const swaggerJson = function (req, res) {
  res.setHeader('Content-Type', 'application/json');
  res.send(swaggerSpec);
};
const swaggerSpec = swaggerDoc(options);

const swaggerInstall = function (app) {
  if (!app) {
    app = express();
  }
  // 开放相关接口
  app.get('/swagger.json', swaggerJson);
  // 使用 swaggerSpec 生成 swagger 文档页面，并开放在指定路由
  app.use('/swagger', swaggerUI.serve, swaggerUI.setup(swaggerSpec));
};
module.exports = swaggerInstall;

```

主入口js文件

```js
// 使用swagger API 文档
const swaggerInstall = require('./utils/swagger/index');
swaggerInstall(app);
```





yaml

```js
/**,
 * @swagger
 * deepCharts/apiData/*:
 *    post:
 *      tags:
 *      - 测试
 *      summary: 接口新增修改
 *      produces:
 *      - application/json
 *      parameters:
 *      - name: name
 *        in: query
 *        description: 姓名
 *        required: false
 *        type: integer
 *        maximum:
 *        minimum: 1
 *        format:
 *      - name: phone
 *        in: query
 *        description: 电话
 *        required: false
 *        type: integer
 *        maximum:
 *        minimum: 1
 *        format:
 *      responses:
 *        200:
 *          description: successful operation
 *          schema:
 *            ref: #/definitions/Order
 *        400:
 *          description: Invalid ID supplied
 *        404:
 *          description: Order not found
 * */
```

