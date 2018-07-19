### CentOS 7 默认没有使用iptables，所以通过编辑iptables的配置文件来开启80端口是不可以的
### CentOS 7 采用了 firewalld 防火墙
如要查询是否开启80端口则：
```
# firewall-cmd --query-port=80/tcp
no
```
上面的结果`no`说明80端口没有开启

开启80端口:
```
# firewall-cmd --add-port=80/tcp
success
```
