## 纯前端 knife4j-vue3 

- 1、修改 `knife4j-vue3/src/layouts/BasicLayout.vue` 中的 `initKnife4jFront` 方法

- 2、将 `url` 地址修改为其的服务的 `service.json` 路由或者文件

```javascript
function initKnife4jFront() {
  //该版本区别于Spring-ui的版本,提供给其它语言来集成knife4j
  const i18nParams = getI18nFromUrl()
  const tmpI18n = i18nParams.i18n
  const swaggerOptions = {
    routeParams: route.params,
    plus: getPlusStatus(),
    i18n: tmpI18n,
    localStore: localStore,
    configSupport: false,
    i18nInstance: getCurrentI18nInstance(),
    //覆盖url地址,多个服务的组合
    url: "http://127.0.0.1/services.json"
  }
  initSwagger(swaggerOptions);
}
```

- 3、`services.json` 的示例值，更局需要修改

```js
[
  {
    "name": "项目名称",
    "url": "http://127.0.0.1/doc/swagger.json",
    "swaggerVersion": "2.0",
    "location": "http://127.0.0.1/doc/swagger.json"
  }
]
```

- 4、编辑 `.env.development` 文件
  
```js
# 发行版本类型 可选值: SpringDocOpenApi | Knife4jSpringUi | Knife4jJFinal | Knife4jFront
VITE_RELEASE_APP_TYPE = 'Knife4jFront'
```

#### 安装
```
pnpm install
```

#### 开发
```
pnpm dev
```
访问 `http://localhost:5173/doc.html`

#### 打包
```
pnpm build
```