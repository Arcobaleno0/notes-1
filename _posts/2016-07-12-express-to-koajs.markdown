---
layout: post
title:  "Express to Koajs"
date:   2016-07-12 16:40:00 +0800
categories: koajs express
---

<style>
table {
    border-collapse: collapse;
}
table td, table th {
    border: solid 1px #ccc;
    padding: 8px;
}
table tr:odd {
  background: #f00;
}
table tbody tr:nth-child(2n + 1) {
  background: rgba(215, 212, 212, 0.35);
}
</style>

## Express to Koa


|---
| Express | Koa
|:-|:-
| var express = require('express'), <br> router = express.Router();| var router = require('koa-router')();
| module.exports = router | module.exports = router.routes()
| function(req, res) | function* ()
| router.get('/:id') //relative path | router.get('/test/:id') // fullpath
| res.render('') | this.render('')
| res.redirect('') | this.redirect('')
| res.end('') | this.body = ''
| req.headers['key'] | this.request.headers['key']
| req.params['key'] | this.params['key']
| req.query['key'] | this.query['key']
| res.cookie(key, value, options) | this.cookies.set(key, value, options)
| req.cookies['key'] | this.cookies.get('key', options)
| req.body | this.request.body
| value = method(params, callback) | value = yield method(params)
