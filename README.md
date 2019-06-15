# hpServer
hpServer 是 aardio 编写的，基于 hpsocket 的 HTTP 服务端。
hpServer 内置有线程池及消息池，便于处理执行时间较长的请求。

hpServer 的 onThreadCreated/onRequest/onThreadEnd 应该在线程创建前设置完毕，并调用updateThreadCall（）。

start 函数默认将启动最低线程数，减少响应时间。

onRequest 返回了 request,response 两个对象。

对于HTTP请求，request , response 的用法基本与 fastcgi 中的一致，但这只是简单模仿，如果有Bug，请反馈。

对于WS消息，request，response 基本与 httpAgent 返回的消息，wsTask 一致。
具体见 message.wsMessageSimple, message.websocketTask。

目前每个线程会造成 5 个字节的内存泄漏，有兴趣的可以帮忙核实一下。
