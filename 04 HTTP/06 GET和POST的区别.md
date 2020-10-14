# GET和POST的区别
GET和POST是HTTP协议中发送请求的两种方法，底层都是基于TCP/IP的，本质上都是TCP连接，没什么区别，由于HTTP和浏览器/服务器的限制，导致他们在应用过程中有一些不同。   
1. GET产生一个TCP包，一次性将header和data发送给服务器，POST产生两个TCP包，第一次将header发送给服务器，得到服务器同意（100connection）后，再讲data发给服务器。   
1. 语义区别，GET是获取数据，POST传输数据。   
1. GET在浏览器回退时是无害的，而POST会再次提交请求。   
1. GET产生的URL地址可以被Bookmark，而POST不可以。   
1. GET请求会被浏览器主动cache，而POST不会，除非手动设置。  
1. GET请求只能进行url编码，而POST支持多种编码方式。   
1. GET请求参数会被完整保留在浏览器历史记录里，而POST中的参数不会被保留。   
1. GET请求在URL中传送的参数是有长度限制的，而POST么有。   
1. 对参数的数据类型，GET只接受ASCII字符，而POST没有限制。   
1. GET比POST更不安全，因为参数直接暴露在URL上，所以不能用来传递敏感信息。   
1. GET参数通过URL传递，POST放在Request body中。