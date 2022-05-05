# Linux 常用命令手册
## 1.文件传输
  ### 1. bye
      功能说明：中断 FTP 连线并结束程序。
      语 法：bye 
      补充说明：在 ftp 模式下，输入 bye 即
      可中断目前的连线作业，并结束 ftp 的执行。
  ### 2. ftp(file transfer protocol) 
  ### 3. ftpcount
  ### 4.ftpshut(ftp shutdown)
  ### 5. ftpwho
  ### 6. ncftp(nc file transfer protocol)
  ### 7. tftp(trivial file transfer protocol)
  ### 8. uucico
  ### 9. uucp
  ### 10. uupick
  ### 11. uuto



# Kali 常用命令手册

## kali工具arpspoof

### 局域网断网攻击
#### arpspoof  -i 网卡 -t 目标ip 网关

## kali工具wireshark

### 过滤源ip、目的ip
#### ip.src==192.168.63.242 （只监听某个ip地址）发送方
#### ip.dst==192.168.63.242 （只监听某个ip地址）接收方

### 端口过滤
#### tcp.port==80     （源端口和目的端口）
#### tcp.srcport==80  （源端口）
#### tcp.dstport==80  （目的端口）

### http模式过滤
#### http.request.method=="GET"
#### http.request.method=="POST"

### 连接符and
ip.src==192.168.63.242 and http and tcp.port==80