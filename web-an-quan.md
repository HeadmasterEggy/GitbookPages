# Web安全

## 信息搜集

### 信息搜集的重要性

古人云“知己知彼，百战不殆”，在现实世界和比赛中，信息搜集是前期的必备工作，也是重中之重。在CTF线上比赛的Web类题目中，信息搜集涵盖的面非常广，有备份文件、目录信息、Banner信息等，这就需要参赛者有丰富的经验，或者利用一些脚本来帮助自己发现题目信息、挖掘题目漏洞。本节会尽可能叙述在CTF线上比赛中Web类题目包含的信息搜集，也会推荐一些作者测试无误的开源工具软件。\
因为信息搜集大部分是工具的使用（git泄露可能涉及git命令的应用），所以本章可能不会有太多的技术细节。同时，因为信息搜集的种类比较多，本章会尽可能地涵盖，如有不足之处还望理解；最后会通过比赛的实际例子来体现信息搜集的重要性。

### 信息搜集的分类

前期的题目信息搜集可能对于解决CTF线上比赛的题目有着非常重要的作用，下面将从敏感目录、敏感备份文件、Banner识别三方面来讲述基础的信息搜集，以及如何在CTF线上比赛中发现解题方向。

### 敏感目录泄露

通过敏感目录泄露，我们往往能获取网站的源代码和敏感的URL地址，如网站的后台地址等。

### git泄露

【漏洞简介】git是一个主流的分布式版本控制系统，开发人员在开发过程中经常会遗忘.git文件夹，导致攻击者可以通过.git文件夹中的信息获取开发人员提交过的所有源码，进而可能导致服务器被攻击而沦陷。\
（1）常规git泄露\
常规git泄露：即没有任何其他操作，参赛者通过运用现成的工具或自己编写的脚本即可获取网站源码或者flag\
工具:

#### 本地docker搭建web环境

#### [常见的搜集](https://book.nu1l.com/tasks/#/pages/web/1.1?id=%e5%b8%b8%e8%a7%81%e7%9a%84%e6%90%9c%e9%9b%86)

**题目描述:**

一共3部分flag

**docker-compose.yml**

```yaml
version: '3.2'

services:
  web:
    image: registry.cn-hangzhou.aliyuncs.com/n1book/web-information-backk:latest
    ports:
      - 80:80
```

**启动方式**

docker-compose up -d

![image.png](https://cdn.nlark.com/yuque/0/2023/png/28161567/1681038144557-a1406192-6a85-4c14-8eb9-5ac829e1183c.png#averageHue=%23f4f4f4\&clientId=ud68174ae-9c37-4\&from=paste\&height=290\&id=u41eb8dfe\&name=image.png\&originHeight=580\&originWidth=2570\&originalType=binary\&ratio=2\&rotation=0\&showTitle=false\&size=85650\&status=done\&style=none\&taskId=ue5603dcb-d34c-4e99-826a-6040e35c281\&title=\&width=1285)\
用**dirsearch**扫一下\
![image.png](https://cdn.nlark.com/yuque/0/2023/png/28161567/1681038911744-f46386fc-7dd0-475a-9153-46e113142c69.png#averageHue=%23fdfdfd\&clientId=ud68174ae-9c37-4\&from=paste\&height=629\&id=ub9c24e96\&name=image.png\&originHeight=1258\&originWidth=1528\&originalType=binary\&ratio=2\&rotation=0\&showTitle=false\&size=295783\&status=done\&style=none\&taskId=u5717c0b9-72ac-4f46-8c69-8c20f09e1a1\&title=\&width=764)

可以看见三个目录可以访问

```http
/.index.php.swp
/index.php~
/.robots.txt
```

分别访问可以看到3个flag

```http
flag1:n1book{info_1 
flag2:s_v3ry_im
flag3:p0rtant_hack}
```

**题目Flag**

> **n1book{info\_1s\_v3ry\_imp0rtant\_hack}**

#### [粗心的小李](https://book.nu1l.com/tasks/#/pages/web/1.1?id=%e7%b2%97%e5%bf%83%e7%9a%84%e5%b0%8f%e6%9d%8e)

**题目描述:**

看看能不能找到信息吧？

**docker-compose.yml**

```yaml
version: '3.2'

services:
  web:
    image: registry.cn-hangzhou.aliyuncs.com/n1book/web-information-git:latest
    ports:
      - 80:80
```

**启动方式**

docker-compose up -d

![image.png](https://cdn.nlark.com/yuque/0/2023/png/28161567/1681040349550-b0ccaca2-aa7d-4800-889b-872ff71b6f63.png#averageHue=%23f1f1f1\&clientId=ud68174ae-9c37-4\&from=paste\&height=325\&id=uc4a611d5\&name=image.png\&originHeight=650\&originWidth=2138\&originalType=binary\&ratio=2\&rotation=0\&showTitle=false\&size=126216\&status=done\&style=none\&taskId=u74ec95fd-12e3-4833-befd-3d36ec49397\&title=\&width=1069)\
访问[http://127.0.0.1/.git/](http://127.0.0.1/.git/config)发现没东西\
再访问[http://127.0.0.1/.git/config](http://127.0.0.1/.git/config)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/28161567/1681040411116-e1adbe04-19e8-45bd-8303-1f02694c3402.png#averageHue=%231f1f1f\&clientId=ud68174ae-9c37-4\&from=paste\&height=181\&id=uac2972c3\&name=image.png\&originHeight=362\&originWidth=822\&originalType=binary\&ratio=2\&rotation=0\&showTitle=false\&size=45773\&status=done\&style=none\&taskId=u9c7f4699-e3aa-4e2b-8c72-b2aea0a63fa\&title=\&width=411)\
用**scrabble**扫一下试试\
![image.png](https://cdn.nlark.com/yuque/0/2023/png/28161567/1681040522538-f929b25d-0e7f-4438-9cb5-6368f878a5a0.png#averageHue=%23161616\&clientId=ud68174ae-9c37-4\&from=paste\&height=177\&id=uc1e6a9e5\&name=image.png\&originHeight=354\&originWidth=1152\&originalType=binary\&ratio=2\&rotation=0\&showTitle=false\&size=86502\&status=done\&style=none\&taskId=uaa231076-e8b6-4cad-be88-1e663043e37\&title=\&width=576)\
**Githack**也可以\
![image.png](https://cdn.nlark.com/yuque/0/2023/png/28161567/1681047131033-9ff0ad7e-f57f-4682-aebd-fac6c539ed5c.png#averageHue=%23040404\&clientId=ud68174ae-9c37-4\&from=paste\&height=377\&id=u189dc2f9\&name=image.png\&originHeight=754\&originWidth=1842\&originalType=binary\&ratio=2\&rotation=0\&showTitle=false\&size=127274\&status=done\&style=none\&taskId=ub3e4a2fb-f072-4af3-a4b2-fc57338362d\&title=\&width=921)\
本地查看发现生成了**index.html**文件\
![image.png](https://cdn.nlark.com/yuque/0/2023/png/28161567/1681040729553-c1693ecf-3f88-4b5e-bace-948e5701c65b.png#averageHue=%23060606\&clientId=ud68174ae-9c37-4\&from=paste\&height=77\&id=u14993292\&name=image.png\&originHeight=154\&originWidth=662\&originalType=binary\&ratio=2\&rotation=0\&showTitle=false\&size=18913\&status=done\&style=none\&taskId=u0e5120e5-add8-4167-aeb9-2ba24b335a1\&title=\&width=331)\
查看发现flag\
![image.png](https://cdn.nlark.com/yuque/0/2023/png/28161567/1681040794609-70618175-2293-488a-82d3-9e2c672b6ffe.png#averageHue=%230a191e\&clientId=ud68174ae-9c37-4\&from=paste\&height=824\&id=ub6e1a914\&name=image.png\&originHeight=1648\&originWidth=2746\&originalType=binary\&ratio=2\&rotation=0\&showTitle=false\&size=455725\&status=done\&style=none\&taskId=u0644060c-e8b7-4a7e-8311-a45e2867589\&title=\&width=1373)

**题目Flag**

n1book{git\_looks\_s0\_easyfun}

#### CTFhub **Index**

![image.png](https://cdn.nlark.com/yuque/0/2023/png/28161567/1681116675416-97366da6-c0e9-4327-9774-fa02daa3540a.png#averageHue=%23f3e0eb\&clientId=u51818e46-9fdb-4\&from=paste\&height=63\&id=G3hAW\&name=image.png\&originHeight=126\&originWidth=939\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=38507\&status=done\&style=none\&taskId=u7a8ef003-c2d0-428c-9836-1076fd2b9fe\&title=\&width=469.5)\
然后Githack\
![image.png](https://cdn.nlark.com/yuque/0/2023/png/28161567/1681116713380-e442c73d-59d0-4167-8f79-2d5c922a41fb.png#averageHue=%23f6f6f6\&clientId=u51818e46-9fdb-4\&from=paste\&height=84\&id=nGXPr\&name=image.png\&originHeight=168\&originWidth=714\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=26831\&status=done\&style=none\&taskId=u6b268a2c-01fa-4577-84d8-a1c4d4f256d\&title=\&width=357)\
flag就有了\
![image.png](https://cdn.nlark.com/yuque/0/2023/png/28161567/1681116747302-22201999-4325-4be4-9fcb-dbc0f9174e05.png#averageHue=%23f7f7f7\&clientId=u51818e46-9fdb-4\&from=paste\&height=119\&id=CqyZH\&name=image.png\&originHeight=237\&originWidth=662\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=37151\&status=done\&style=none\&taskId=u16e856b9-64ed-47e1-9230-04de38b1018\&title=\&width=331)

#### git回滚

git作为一个版本控制工具，会记录每次提交（commit）的修改，所以当题目存在git泄露时，flag（敏感）文件可能在修改中被删除或被覆盖了，这时我们可以利用git的**git reset**命令来恢复到以前的版本。\
除了使用“git reset”，更简单的方式是通过“git log-stat”命令查看每个commit修改了哪些文件，再用“git diff HEAD commit-id”比较在当前版本与想查看的commit之间的变化。

#### git泄露的其他利用

除了查看源码的常见利用方式，泄露的git中也可能有其他有用的信息，如.git/config文件夹中可能含有access\_token信息，从而可以访问这个用户的其他仓库。

**SVN泄露**

SVN（subversion）是源代码版本管理软件，造成SVN源代码漏洞的主要原因是管理员操作不规范将SVN隐藏文件夹暴露于外网环境，可以利用.svn/entries或wc.db文件获取服务器源码等信息。这里推荐两个工具：

**描述**

**SVN（subversion）是程序员常用的源代码版本管理软件。一旦网站出现SVN**漏洞，其危害远比SQL注入等其它常见网站漏洞更为致命，因为黑客获取到网站源代码后，一方面是掠夺了网站的技术知识资产，另一方面，黑客还可通过源代码分析其它安全漏洞，从而对网站服务器及用户数据造成持续威胁。更严重的问题在于，**SVN**产生的 **.svn 目录下还包含了以 .svn-base 结尾的源代码文件副本（低版本SVN具体路径为text-base**目录，高版本**SVN**为**pristine**目录），如果服务器没有对此类后缀做解析，黑客则可以直接获得文件源代码。

**具体来说：**

1. 在使用SVN管理本地代码过程中，会自动生成一个隐藏文件夹，其中包含重要的源代码信息。但一些网站管理员在发布代码时，不愿意使用‘导出’功能，而是直接复制代码文件夹到WEB服务器上，这就使隐藏文件夹被暴露于外网环境，这使得渗透工程师可以借助其中包含版本信息追踪的网站文件，逐步摸清站点结构。
2. 在服务器上布署代码时。如果是使用 **svn checkout** 功能来更新代码，而没有配置好目录访问权限，则会存在此漏洞。黑客利用此漏洞，可以下载整套网站的源代码。
3. \*\*.svn \*\*目录（隐藏目录）使用 \*\*svn checkout \*\*后，项目目录下会生成隐藏的 \*\*.svn \*\*文件夹（\*\*Linux \*\*上用 \*\*ls \*\*命令看不到，要用 \*\*ls -al \*\*命令）。**svn1.6**及以前版本会在项目的每个文件夹下都生成一个 \*\*.svn \*\*文件夹，里面包含了所有文件的备份，文件名为 \*\*.svn/text-base/ \*\*文件名 **.svn-base**。**svn1.7**及以后版本则只在项目根目录生成一个 \*\*.svn \*\*文件夹，里面的 \*\*pristine \*\*文件夹里包含了整个项目的所有文件备份。

**CTFhub SVN泄露**

先用dirsearch扫出来\
![image.png](https://cdn.nlark.com/yuque/0/2023/png/28161567/1681116929131-75536078-9ca2-4f1c-b062-148819ede0f6.png#averageHue=%23e6f6fd\&clientId=u51818e46-9fdb-4\&from=paste\&height=98\&id=u3faaa850\&name=image.png\&originHeight=195\&originWidth=825\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=50102\&status=done\&style=none\&taskId=u47db7e25-eef3-4bf8-9005-d3c66df0c0a\&title=\&width=412.5)\
dvcs-ripper再扫\
![image.png](https://cdn.nlark.com/yuque/0/2023/png/28161567/1681117127099-9b7d7e75-73f8-41b4-bab9-7d218cc15933.png#averageHue=%232e0d24\&clientId=u51818e46-9fdb-4\&from=paste\&height=174\&id=u3ed6722e\&name=image.png\&originHeight=348\&originWidth=1138\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=153325\&status=done\&style=none\&taskId=ubd6e4f0c-9c49-4356-b8c4-be0acaa95a8\&title=\&width=569)\
提示flag在旧版本\
`ls -a`进入`.svn`\
![image.png](https://cdn.nlark.com/yuque/0/2023/png/28161567/1681117291554-00e6b960-6e26-4c54-bca0-7f43d36f5f4c.png#averageHue=%232e0d24\&clientId=u51818e46-9fdb-4\&from=paste\&height=110\&id=u8782fe5a\&name=image.png\&originHeight=220\&originWidth=1139\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&size=167710\&status=done\&style=none\&taskId=u2f668193-36ba-4628-9a27-248671cab4a\&title=\&width=569.5)

**HG泄露**

在初始化项目时，HG会在当前文件夹下创建一个.hg隐藏文件夹，其中包含代码和分支修改记录等信息。这里推荐工具：

**总结经验**

不论是.git这些隐藏文件，还是实战中的admin之类的敏感后台文件夹，其关键在于字典的强大，读者可以在某些工具的基础上进行二次开发，以满足自己需要。这里推荐一个开源的目录扫描工具：\
CTF线上比赛往往会有重定向一类问题。例如，只要访问.git，便会返回403，此时试探着访问.git/config，如果有文件内容返回，就说明存在git泄露，反之，一般不存在。而在SVN泄露中，一般是在entries中爬取源代码，但有时会出现entries为空的情况，这时注意wc.db文件存在与否，便可通过其中的checksum在pristine文件夹中获取源代码。

**robots.txt**

robots协议也称爬虫协议、爬虫规则等,是指网站可建立一个robots.txt文件来告诉搜索引擎哪些页面可以抓取,哪些页面不能抓取,而搜索引擎则通过读取robots.txt文件来识别这个页面是否允许被抓取。简单来说就是网站里面放了robots.txt，来对爬虫说，我的网站这些路径不允许爬取。但 robots协议没有强制执行力，可以手动在网站域名后面输入robots.txt。 :::tips 例：某ctf 题目不允许爬取/admin/目录，不允许爬取flag.php，不允许爬取www.tar.gz\
User-agent:\* Disallow:/admin/\* Disallow:/flag.php Disallow:/www.tar.gz :::

**.swp文件泄露**

.swp是vi编辑器异常退出，而产生的一个文件比如编辑admin.php异常退出会产生一个admin.php.swp。\
利用方法:如果可以将admin.php.swp下载下来，删掉.swp可以得到admin.php源文件。

**DS\_Store文件泄漏**

.DS\_Store是Mac OS保存文件夹的自定义属性的隐藏文件，如文件的图标位置或背景色，相当于Windows的desktop.ini。 其删除以后的副作用就是这些信息的失去。\
和别人交换文件（或你做的网页需要上传的时候）应该把 .DS\_Store 文件删除比较妥当，因为里面包含了一些你不一定希望别人看见的信息。\
尤其是网站，通过 .DS\_Store 可以知道这个目录里面所有文件的清单，很多时候这是一个不希望出现的问题。\
由于开发/设计人员在发布代码时未删除文件夹中隐藏的.DS\_store，可能造成文件目录结构泄漏、源代码文件等敏感信息的泄露。

**ds\_store\_exp工具**
