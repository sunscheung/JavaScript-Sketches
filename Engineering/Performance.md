### 什么是性能
- 快
  + 加载速度
  + 渲染速度
  + 交互、动画流畅度
- 稳定
- 低耗

### 衡量标准与手段

- Date.now()
- [Navigation Timing](https://www.w3.org/TR/navigation-timing/#sec-navigation-timing-interface)
  + PerformanceTiming
  + PerformanceNavigation
  + window.performance
- [PerformanceResourceTiming](https://www.w3.org/TR/resource-timing/)
- [User Timing](https://www.w3.org/TR/user-timing/)
  + PerformanceMark
  + PerformanceMeasure
  + Performance extensions
- [Performance Observer](https://github.com/bison1994/JavaScript-Sketches/blob/master/Client/Observer.md)
- 渐进式网页指标（Progressive Web Metrics）
  + [英文版](https://codeburst.io/performance-metrics-whats-this-all-about-1128461ad6b)
  + [中文版](https://llp0574.github.io/2017/10/19/performance-metrics-whats-this-all-about/)
- 资源加载时序图分析


### 性能优化的方案体系

目的一：加载速度快
- 网络层
  + 请求的资源尽量少
    - 减少请求次数（雅虎14条之1）
      + 合并资源（spites、Combo Handler）
      + 合并多个 ajax 请求
      + CSS inline
      + 使用 CSS、SVG、Inline Image、Icon-font 代替图片
      + 避免使用 @import 和 iframes
      + 控制域名数量，减少 DNS 查询（雅虎14条之9）
    - 减少重复请求
      + 客户端缓存（雅虎14条之3、13）
      + 利用客户端储存（localStorage）
      + 使用可缓存的 get 请求（雅虎14条之3、14）
    - 减少不必要的请求
      + 移动端字体图标只需要用 ttf
    - 减小资源体积（雅虎14条之4、10）
      + 压缩
      + Gzip
      + 图片优化（渐进式、尺寸适配、剪裁、格式）
      + 根据网络、设备 DPI 加载不同的图片
      + 控制 cookie
    - 只请求当前需要的资源
      + 增量加载（懒加载、渐进式加载、异步加载）
    - 减少无效请求
      + 避免空 src
      + 避免重定向（雅虎14条之11）
    - 减小无效资源（雅虎14条之4、12）
      + 删除无效的代码（可使用浏览器开发工具检测）
  + CDN （雅虎14条之2）
  + 其它协议：UDP、QUIC、SPDY
- 浏览器环境
  + 突破并行加载上限（Domain Sharding、SPDY）
    - PC 端可分片 2-4 个为宜
    - 移动端 DNS 解析很慢，分片不要超过 2 个
  + 提前加载可能将要用到的资源
    - prefetch、prerender
- 交互设计

> [front-end-performance-checklist-2018](https://www.smashingmagazine.com/2018/01/front-end-performance-checklist-2018-pdf-pages/)

> [facebook: bigpipe](https://www.facebook.com/notes/facebook-engineering/bigpipe-pipelining-web-pages-for-high-performance/389414033919/)

> [前端性能优化](https://juejin.im/post/59ff2dbe5188254dd935c8ab)

> [移动 WEB 通用优化策略（一）](http://web.jobbole.com/85673/)

> [移动 WEB 通用优化策略（二）](http://web.jobbole.com/87524/)

> [Web静态资源缓存及优化](https://juejin.im/post/5a098b5bf265da431a42b227)

> [how-medium-does-progressive-image-loading](https://medium.com/@jmperezperez/how-medium-does-progressive-image-loading-fd1e4dc1ee3d)

目标二：渲染速度

- 浏览器环境
  + 关键路径优化（雅虎14条之5、6）
- 代码层
- 交互设计

> [什么阻塞了 DOM](https://juejin.im/post/587f4afb61ff4b00651b3c18)

> [浏览器页面资源加载过程与优化](https://juejin.im/post/5a4ed917f265da3e317df515) from 网易


目标三：交互、动画流畅度

- 浏览器环境
  + 硬件加速
- 代码层
  + 少用 js 动画
  + requestAnimationFrame
  + 合并多个 DOM 操作
  + 函数节流
- 交互设计
  + 动效元素少用阴影和渐变