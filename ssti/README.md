## 靶场介绍
要求getshell

原简介：小明知道这里有漏洞，但他认真修复了原组件的漏洞，你能绕过他的修复吗？

## 相关文章
* [挑战原文](https://暂无)



## 靶场搭建
```bash
iptables -I DOCKER-USER 1 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -I DOCKER-USER 2 -s 172.17.0.0/16 -o eth0 -j DROP

docker build --no-cache -t ssti .
docker run --user nobody -d -p 8078:8078 --name ssti_test ssti
```



