原文链接：<https://baike.baidu.com/item/http%E8%AF%B7%E6%B1%82%E5%A4%B4/6623287?fr=aladdin>
[http相关面试题汇总](https://blog.51cto.com/10808695/1840537)
### 1. 通用首部字段（请求报文与响应报文都会使用的首部字段）
`Date` ：创建报文时间   
`Connection` ：连接的管理   
`Cache-Control` ：缓存的控制   
`Transfer-Encoding` ：报文主体的传输编码方式   
### 2. 请求首部字段（请求报文会使用的首部字段）
`Range` : 获取部分内容   
`Host` : 请求的主机名   
`Connection` : 是否需要持久连接   
`User-Agent` : 产生请求的浏览器类型   
`Referer` : 包含一个URL，用户从该URL代表的页面出发访问当前请求的页面。   
`Accept` : 客户端希望接受的数据类型   
`Accept-Charset`：浏览器可接受的字符集。   
`Accept-Encoding`：浏览器能够进行解码的数据编码方式   
`Accept-Language`：浏览器所希望的自然语言   
`Cookie`：这是最重要的请求头信息之一   
`Content-Type`：主题的对象类型
### 3. 响应首部字段（响应报文会使用的首部字段）
`Accept-Range`：可接受的字节范围   
`Location`：令客户端重新定向到的URI   
`Server`：HTTP服务器的安装信息   

常见的Content-Type：
| Content-Type | 解释 |
|  ----  | ----  |
| text/html | html格式 |
|text/plain|纯文本格式|
|text/css|CSS格式|
|text/javascript|js格式|
|image/gif|gif图片格式|
|image/jpeg|jpg图片格式|
|image/png|png图片格式|
|application/x-www-form-urlencoded|POST专用：普通的表单提交默认是通过这种方式。form表单数据被编码为key/value格式发送到服务器。|
|application/json|POST专用：用来告诉服务端消息主体是序列化后的 JSON 字符串|
|text/xml|POST专用：发送xml数据|
|multipart/form-data|在 Web 表单文件上传时使用|
