# ping_until_success：检查网络通路

ping_until_success是一个bash脚本，将持续ping指定的ip地址直到ping通，脚本里超时时间设置为0.5秒，可根据自身需求进行更改

使用方法如下
```bash
# 直接使用
./ping_until_success 192.168.1.1

# 在其他脚本中使用
source /path/to/ping_until_success
ping_until_success 192.168.1.1
```
