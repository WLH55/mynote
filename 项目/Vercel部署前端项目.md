## Vercel部署前端项目

使用vercel来部署网易云网站（后端接口+前端页面）

SoSalty

已于 2022-09-07 23:39:27 修改

4104
 收藏 43
分类专栏： 前端 文章标签： 前端
版权

前端
专栏收录该内容
12 篇文章1 订阅
订阅专栏
后端接口搭建：
1.GitHub搜索网易云api接口：NeteaseCloudMusicApi

2.点击第一个：



3.进入之后点击fork，将项目保存：



4.回到主页，可以发现此项目已经成功保存：



5.搜索vercel进入其官网，使用GitHub登录好后点击new project：



6.找到刚刚保存的项目，点击import：



 7.填写好项目名字，点击deploy，等待创建



 8.创建成功，出现如下：



 8.点击左边的窗口进入文档，这个URL地址就是我们发请求的baseURL：



 9.在文档里随便找个接口，在此URL后边加上，发现有数据返回，证明可用。至此，后端接口搭建完毕。



 前端网站部署：
1.用vue写好页面，接口功能完善后，也需要将前端项目部署到vercel

2.在根目录新建vercel.json文件，内容：

{
  "rewrites":[{"source":"api/(.*)","destination":"/api"}]
}


 3.在根目录新建api文件夹，里面新建文件index.js，index.js内容：

const express = require('express')
const app = express()
app.use(express.static('../dist'))

module.exports = app
 4.全局安装vercel，终端输入： npm i vercel -g

5.安装好后，终端输入vercel login

6.选择 Log in to Vercel github

7.终端输入：vercel

8.狂点回车键

9.生成一个网址，就是我们部署的网易云：



 10.修改了项目，想要重新部署？终端输入： vercel --prod
————————————————
版权声明：本文为CSDN博主「SoSalty」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/SoSalty/article/details/124516171