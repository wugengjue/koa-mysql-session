koa-mysql-session
=================
this is an adpatation of the logic from the connect mysql-session-store (https://github.com/sugendran/mysql-session-store) to koa-generic-session (https://github.com/koajs/generic-session).

https://www.npmjs.org/package/koa-mysql-session

Usage
=================
npm install koa-mysql-session


example
=================
```js
const koa = require('koa')
    , session = require('koa-generic-session')
    , MysqlStore = require('koa-mysql-session')
    , app = koa() ;

const THIRTY_MINTUES = 30 * 60 * 1000;

const config= {
        user: "someUser",
        password: "somePwd",
        database: "someDatabase",
        host: "someHOst"
}

app.keys = ['your-session-secret']
app.use(session({
        store: new MysqlStore(config),
        rolling: true,
        cookie: {
            maxage:THIRTY_MINTUES
        }
}))
