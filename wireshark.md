
## kali工具wireshark

## 过滤值比较符号
英文|符号|描述|示例
--|:--:|--:|--:
eq|==|等于|ip.src==192.168.1.1
ne|!=|不等于|ip.src!=192.168.1.1
gt|>|大于|frame.len>10
lt|<|小于|frame.len<128
ge|>=|大于等于|frame.len>=100
le|<=|小于等于|frame.len<=100
contains| |包含|sip.TO contains "100"
matches|~|正则匹配|host matche "acme\.(org|com|net)"
bitwise_and|&|位与操作|tcp.flags & 200

## 多个表达式间的组合
英文|符号|描述|示例
--|:--:|--:|--:
and|&&|逻辑与|ip.src==192.168.1.1 and tcp.flags.fin
or||||逻辑或|ip.src==192.168.1.1 or ip.src==192.168.1.2
xor|^^|逻辑异或|tr.dst[0:3] == 0.6.29 xor tr.src[0:3] == 0.6.29
not|!|逻辑非|not llc
[...]| | |
in| | | 


### Protocol (协议) :该选项用来指定协议。可使用的值有ether、fddi、 wlan、 ip、arprarp、decnet、 lat、 sca、 moproc、 mopdl、 tcp和udp.如果没有特别指明是什么协议，则默认使用所有支持的协议。
### Direction (方向) :该选项用来指定来源或目的地，默认使用src or dst作为关键该选项可使用的值有src、dst、 sre and dst和src or dst。
### Host(s): 指定主机地址。如果没有指定，默认使用host 关键字。可能使用的值有net、port、 host 和portrange.
### Logical Operations (逻辑运算):该选项用来指定逻辑运算符。可能使用的值有and和or.其中，not (否)具有最高的优先级; or (或)和and (与)具有优先级，运算时从左至右进行。

### host host
#### host 192.168.63.242

### 过滤源ip、目的ip
#### ip.src==192.168.63.242 （只监听某个ip地址）发送方
#### ip.dst==192.168.63.242 （只监听某个ip地址）接收方
#### ip.addr==192.168.63.242（源地址和目的地地址过滤）
#### !(ip.addr==192.168.63.242)（非源地址和目的地地址过滤）

### 端口过滤
#### tcp.port==80     （源端口和目的端口）
#### udp.port >= 80  
#### tcp.srcport==80  （源端口）
#### tcp.dstport==80  （目的端口）

### http模式过滤
#### http.request.method=="GET"
#### http.request.method=="POST"
#### http.request.code==302 (过滤响应状态码)
#### http.cookid contains 'userid' (指定cookie的http数据包)
#### http && tcp.port==80 or tcp.port==5566
#### http.request.url contains 'User' (请求地址包含'User'的请求)
#### http.host==baidu.com (精确过滤域名)
#### http.host contains 'baidu' (模糊过滤域名)
#### http.content_type == 'text/html'(过滤请求的content_tyoe类型)

### 数据段长度过滤
#### udp.length<20
#### http.content_length <=30

### 连接符and
ip.src==192.168.63.242 and http and tcp.port==80
