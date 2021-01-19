---
title: Koa config
date: 2019-09-29 14:01:32
categories:
- Koa
tags:
- Koa
---


```
const Koa = require('koa')
const Router = require('koa-router')
const serveStatic = require('koa-static')

const path = require('path')
const fs = require('fs')

/** use combinition of koa2-connect and http-proxy-middleware
 *  for 'koa2 proxy middleware'
 */
// const proxy = require('http-proxy-middleware')
// const c2k = require('koa2-connect')
// const proxyMiddleware = config => c2k(proxy(config))

const app = new Koa()
const router = new Router()
const staticPath = path.join(__dirname, 'build')

router.get('/', async (ctx, next) => {
  ctx.response.set('Content-Type', 'text/html; charset=utf-8')
  ctx.response.body = fs.createReadStream(path.join(staticPath, 'index.html'))
  await next()
})

router.get('*', async (ctx, next) => {
  ctx.response.redirect('/')
  await next()
})

/** proxy table */
// router.get('/xxx', proxyMiddleware({
//   target: 'xxx',
//   changeOrigin: true,
//   secure: false
// }))

app.use(serveStatic(staticPath))
app.use(router.routes())
app.use(router.allowedMethods())

app.listen(3000, () => {
  console.log('Koa Server running at: http://localhost:3000')
})
```
