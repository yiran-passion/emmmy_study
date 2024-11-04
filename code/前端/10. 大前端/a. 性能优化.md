## 性能优化指标

- 根据 chrome 最新规则，前端性能优化指标主要有 **FCP(First Contenful Paint)**, **SI(Speed index)**, **LCP(Largest Contentfull Paint)**, **TBT(Total Block Time)**, **CLS(Cumulative Layout Shift)**


### FCP(First Contenful Paint)

- FCP（首次内容绘制）：是指页面从开始加载到页面绘制第一个内容的时间。

- 可以通过以下方式优化 FCP 时间：

  1. 降低服务器响应时间：保证服务器的响应速度，例如使用 CDN 。
  2. 异步加载 script ：使用 async/defer 。

- 理想的 FCP 应该控制在 1.8s 以内


### LCP(Largest Contentfull Paint)

- LCP（最大内容绘制）：是指页面从开始加载到视窗内最大元素完成绘制的时间

- 理想的 LCP 应该控制在 2.5s 以内

### 


## 性能优化方案


### 优化方案

- **1. 启用前端缓存**


- **2. Gzip 压缩**


- **3. 节流函数和防抖函数**


- **4. 异步加载 script 标签**


- **5. 减少重排和重绘**


- **6. 使用合适格式的图片，字体文件使用 woff2 压缩**


- **7. 合并请求，避免接口重复调用，接口数据添加缓存**


- **8. 启用事件委托（事件代理）**


- **9. 使用懒加载**


- **10. 骨架屏**