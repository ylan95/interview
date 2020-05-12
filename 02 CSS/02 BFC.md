## 概念
块级格式化上下文
## 原理
* bfc区域内部元素在垂直方向上依次排列
* 同一个bfc区域内，两个相邻元素在垂直方向上的margin会发生重叠
* bfc区域与外界区域隔绝，互不干扰
* 计算bfc区域高度时，浮动元素参与计算
* bfc区域与float区域不会发生重叠
## 触发方式
* 根元素
* display:inline-block,flex,inline-flex,table-cell，table-caption
* position:absolute,fixed
* float:left/right
* overflow不为visible