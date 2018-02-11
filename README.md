## 项目简介

基于 vue.js 的前端开发环境，用于前后端分离后的单页应用开发，可以在开发时使用 ES Next、scss 等最新语言特性。项目包含：

- 基础库: `vue.js`、`vue-router`、`vuex`
- 编译/打包工具：`webpack`、`babel`、`node-sass`
- 本地服务器：`express`

## 命令列表：

    #开启本地开发服务器，监控项目文件的变化，实时构建并自动刷新浏览器，浏览器访问 http://localhost:1990
    npm run dev

    #使用生产环境配置构建项目，构建好的文件会输出到 "dist" 目录，
    npm run build

    #运行构建服务器，可以查看构建的页面
    npm run build-server
    
## 前后端分离
项目基于 spa 方式实现前后端分离，服务器通过 nginx 区分前端页面和后端接口请求，分发到不同服务。前端物理上只有一个入口页面, 路由由前端控制（基于vue-router），根据不同的 url 加载相应数据和组件进行渲染。

## 接口 mock
前后端分离后，开发前需要和后端同学定义好接口信息（请求地址，参数，返回信息等），前端通过 mock 的方式，即可开始编码，无需等待后端接口 ready。
项目的本地开发服务器是基于 express 搭建的，通过 express 的中间件机制，我们已经在 dev-server 中添加了接口 mock 功能。
开发时，接口的 mock 数据统一放在 mock 目录下，每个文件内如下：

    module.exports = {
    
      // 接口地址
      api: '/api/hello',
    
      // 返回数据 参考http://expressjs.com/zh-cn/4x/api.html
      response: function (req, res) {
        res.send(`
          <p>hello vue!</p>
        `);
      }
    }

## 联调方式

前后端分离后，由于服务端和前端的开发环境处于2台不同的机器上，前端的异步请求需要代理到后端机器中。
联调的时候，只需通过 proxy 参数运行 dev 脚本即可，所有 mock 目录下定义的接口将会转发到 proxy 参数指定的机器.

