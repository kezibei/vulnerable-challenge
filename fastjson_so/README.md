## 靶场介绍
要求getshell
这个靶场主要考的是fastjson 1.2.78在jdk11，没有io的情况下如何写文件，以及springboot环境不知道jdk路径的情况下如何通过写文件getshell。
原简介：小明作为开发员，虽然知道fastjson版本过低存在漏洞，但因为兼容性问题没法升级fastjson。但他仔细看了漏洞利用过程，觉得是io组件和jdk版本的问题，于是他删除了io并升级到jdk11。那么你还能利用成功吗？



## 相关文章
* [挑战原文](https://mp.weixin.qq.com/s/HfOaAz3A16nesIcdLkoUkA)
* [fastjson链](https://mp.weixin.qq.com/s/H0_UqhyCT7pDa6Szc7rNAQ)
* [劫持so](https://mp.weixin.qq.com/s/NrNFwEfNbqGKd5jUSe-4eA)
* [触发so](https://mp.weixin.qq.com/s/yF1zeXGPEnDzMosAssqAlQ)

## 靶场搭建
```bash
docker build --no-cache -t fj_plus:randomjdk .
docker run -d -p 8078:8078 --name fj_test fj_plus:randomjdk
```




