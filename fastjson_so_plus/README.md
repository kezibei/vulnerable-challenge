## 靶场介绍
因为fastjson_so靶场出现了大量的非预期，所以对靶场环境进行加固，包括不出网，不允许劫持大部分so，不再回显等等。但依旧存在部分非预期。

## 相关文章
* [挑战原文](https://mp.weixin.qq.com/s/HfOaAz3A16nesIcdLkoUkA)
* [fastjson链](https://mp.weixin.qq.com/s/H0_UqhyCT7pDa6Szc7rNAQ)
* [劫持so](https://mp.weixin.qq.com/s/NrNFwEfNbqGKd5jUSe-4eA)
* [触发so](https://mp.weixin.qq.com/s/yF1zeXGPEnDzMosAssqAlQ)

## 靶场搭建
```bash
iptables -I DOCKER-USER 1 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -I DOCKER-USER 2 -s 172.17.0.0/16 -o eth0 -j DROP

docker build --no-cache -t fj_plus:randomjdk .
docker run --cap-drop ALL --security-opt no-new-privileges -d -p 8078:8078 --name fj_test fj_plus:randomjdk
```



