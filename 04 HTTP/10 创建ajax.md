## 创建xmlhttp对象
```
var xmlhttp;
if(window.XMLHttpRequest){
    xmlhttp = new XMLHttpRequest()
}else{
    xmlhttp = new ActiveXObject('Microsoft.XMLHTTP')
}
```
## 发送 GET 请求
```
xmlhttp.open("GET",url?t=123,async)
xmlhttp.send()
```
## 发送 POST 请求
```
xmlhttp.open("POST",url,async)
xmlhttp.setRequestHeader(header,value)
xmlhttp.send('key=value&key=valu')
```
## onreadystatechange
readystate 每次变化，都会触发 onreadystatechange 事件
## readystate
* 0 请求未初始化
* 1 服务器已建立连接
* 2 请求已接收
* 3 请求处理中
* 4 请求处理完成且响应已就绪
