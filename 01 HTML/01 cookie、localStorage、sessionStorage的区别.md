
## cookie、localStorage、sessionStorage的区别

名称|大小|默认随请求发送|操作方式|过期时间|作用域
-|-|-|-|-|-
cookie|4k|是|document.cookie|按照设置的过期时间，如果未设置，关闭浏览器窗口时cookie失效|同域共享
localStorage|更大容量，标准5M|否|setItem,getItem等|没有过期时间，如果不手动清除，数据就永远不会过期|同域共享
sessionStorage|更大容量，标准5M|否|setItem,getItem等|浏览器窗口关闭即失效|标签页