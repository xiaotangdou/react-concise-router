# react-concise-router

A concise router base on [react-router v4.x](https://github.com/ReactTraining/react-router).

> 未发布！！！

```ls
npm install -S react-concise-router
```
**Required**

```ls
npm install -S react-router
```

```ls
npm install -S react-router-dom
```

## use

**router.js**

```js
import Router from 'react-concise-router'
import Home from './views/Home'
import User from './views/User'
import UserInfo from './views/UserInfo'
import Error from './views/Error'
import view from './views/admin/view'
import Dashboard from './views/admin/Dashboard'

export default new Router ({
  routes: [
    {path: '/', component: Home},
    {path: '/user', component: User},
    {path: '/user/:userId', component: UserInfo},
    {
      path: '/admin',
      component: view,
      name: 'admin-view',

      children: [
        {path: '/', component: Dashboard},
        {component: Error}
      ]
    },
    {path: '*', component: Error},
  ]
})

```

**App.jsx**

```jsx
import React from 'react'
import router from './router'

export default class App extends React.Component {
  render () {
    return (
      <div>
        <p>wellcome !</p>
        <router.view />
      </div>
    )
  }
}

```

## API

```js
import Router from 'react-concise-router'
```

**new Router(options)** 创建路由对象，返回router。



+ **<router.view />** 路由出口。
  - **props.name** string 路由出口子名称，在 `options.routes[].name` 设置。

+ **<router.link to={{}}>xxx</router.link>** object|string 路径或者路径对象。

+ **router.route(route)** 生成url，用于history.push。

+ **router.beforeEach(cxt, next)** 路由切换中间件

