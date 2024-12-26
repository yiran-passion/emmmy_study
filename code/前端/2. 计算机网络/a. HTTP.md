
## HTTP0.9


## HTTP1.0


## HTTP1.1

#### 相较于 HTTP1.0 进行了优化

- 使用 TCP 持久连接。
- 浏览器为每个域名最多维持 6 个 TCP 持久连接。
- 使用 CDN 实现域名分片机制。

#### HTTP1.1 存在的问题

- TCP 的慢启动。
- 多个 TCP 连接竞争固定的带宽，导致每个 TCP 连接带宽不足。
- 会造成队头阻塞问题。


## HTTP2


## HTTP3


## HTTPS


## HTTP headers


## HTTP Response Code

```js
export default {
  // 2XX 成功状态码
  '200 (Bad Request)': '请求成功',
  // 3XX 资源重定向状态码
  '301 (Moved Permanently)': '资源被永久重定向到新地址。',
  '302 (Found)': '资源被临时重定向到新地址。',
  '304 (Not Modified)': '向缓存服务器法器请求，命中协商缓存。',
  // 4XX 客户端错误状态码
  '400 (Bad Request)': '表示请求格式错误。（例如请求参数错误、请求方法错误、请求头错误等）',
  '401 (Unauthorized)': '表示客户端请求需要鉴权，并且服务器授权失败。（例如 token 失效）',
  '403 (Forbidden)': '表示客户端有请求，但是服务端禁止访问。',
  '404 (Not Found)': '表示服务端找不到客户端请求资源。',
  // 5XX 服务端错误状态码
  '500 (Internal Server Error)': '表示服务器在请求时遇到了内部错误。（例如后端代码有问题、数据库问题等）',
  '502 (Bad Getaway)': '表示服务器在响应时出现了问题。',
  '503 (Service Unavailable)': '表示服务器无法提供服务。（例如服务器正在维护、正在发版等）'
}
```