### 事件类型

- UIEvent
- CustomEvent
- MutationEvent


- 鼠标
- 键盘
- 表单
- 拖放
- 触摸
- 动画
- 设备
- DOM mutation
- window


### 事件流 Flow
1. 捕获（capture phase）：从 Window 对象查询到目标节点父元素
2. 目标（target phase）：在目标节点上触发
3. 冒泡（bubbling phase）：从目标节点父元素传导至 Window 对象


### 事件代理 Delegation
- 作用
  + 减少事件绑定数量
  + 使用根元素代理事件，避免捕获、冒泡等繁琐流程，减少节点查询路径，可提高事件触发的灵敏度

> “捕获阶段提供了在事件查询传播到目标之前将其拦截（捕获）的机会” ———— 《JavaScript 权威指南》

- 存在的问题
  + 可能增加事件系统复杂度，捕获阶段还是冒泡阶段？子元素事件是否屏蔽父元素代理？
  + 目标对象 target 如果 DOM 结构比较复杂，那么 target 的取值可能不精确，因而不适用