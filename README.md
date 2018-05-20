# Analysis of Wechat history
### 运行环境
Python3  
### 功能说明
获取微信聊天记录，分析词频并根据词频生成对应外形的词云图  

### 环境配置
openpyxl
>pip install openpyxl

对于Python中生成词云，需要安装WordCloud，他的安装不像上面的简单，如果只是通过pip安装的话会出现很多莫名其妙的错误。
>下载相应版本的whl文件，从http://www.lfd.uci.edu/~gohlke/pythonlibs/#wordcloud  
进入相应文件件  
在管理员环境下运行python -m pip install <filename>    

其余的所需环境不再一一赘述，请缺少的自行谷歌百度搜索安装。

### 使用步骤
##### 一.获取微信聊天记录
1.有一部已经ROOT的安卓手机（IOS系统获取微信聊天记录比较简单不再赘述）
2.获取聊天记录的保存文件
/data/data/com.tencent.mm/MicroMsg/一大串长文件夹/EnMicroMsg.db<img src="https://pic3.zhimg.com/50/ed4f329a917b79dd7f3f87248416b2d3_hd.jpg" data-rawwidth="433" data-rawheight="220" class="origin_image zh-lightbox-thumb" width="433" data-original="https://pic3.zhimg.com/ed4f329a917b79dd7f3f87248416b2d3_r.jpg">
这文件存放着微信聊天记录，把它拷贝到根目录，接着拷贝到电脑桌面
<img src="https://pic1.zhimg.com/50/7866aa801ad545950e5323af5a77a13b_hd.jpg" data-rawwidth="98" data-rawheight="116" class="content_image" width="98">
3.对聊天记录文件进行解锁
钥匙 KEY = IMEI （手机序列号） + UIN（用户信息号）手机输入 *#06#  能得到IMEI<img src="https://pic3.zhimg.com/50/4464ea95eefb33d5c552e023446a2c9e_hd.jpg" data-rawwidth="303" data-rawheight="346" class="content_image" width="303">在哪里找到UIN呢？文件路径：/data/data/com.tencent.mm/shared_prefs/system_config_prefs.xml<img src="https://pic2.zhimg.com/50/44d61c472ccae9e7e0651adf7bb2e2e2_hd.jpg" data-rawwidth="433" data-rawheight="223" class="origin_image zh-lightbox-thumb" width="433" data-original="https://pic2.zhimg.com/44d61c472ccae9e7e0651adf7bb2e2e2_r.jpg">拷贝到电脑，右键记事本打开，uin在最下面<img src="https://pic3.zhimg.com/50/5305bf089e39639e4626403a2112f812_hd.jpg" data-rawwidth="606" data-rawheight="125" class="origin_image zh-lightbox-thumb" width="606" data-original="https://pic3.zhimg.com/5305bf089e39639e4626403a2112f812_r.jpg">钥匙 KEY= IMEI （手机序列号） + UIN（用户信息号）=  864587027946418-1342131695 把这一层拷贝到网站计算MD5值， 网站地址：免费 MD5 散列计算器<img src="https://pic2.zhimg.com/50/b091f56ce1a620c843201f230440936c_hd.jpg" data-rawwidth="500" data-rawheight="260" class="origin_image zh-lightbox-thumb" width="500" data-original="https://pic2.zhimg.com/b091f56ce1a620c843201f230440936c_r.jpg">
把前7位拷贝下来当做钥匙KEY：69fd600

4.下载打开数据库的软件SQLite Database Browser，打开如下<img src="https://pic2.zhimg.com/50/5bf2e3360a7112a21e70b23147441416_hd.jpg" data-rawwidth="704" data-rawheight="374" class="origin_image zh-lightbox-thumb" width="704" data-original="https://pic2.zhimg.com/5bf2e3360a7112a21e70b23147441416_r.jpg">点击File，OpenDatabase，选择刚才的EnMicroMsg.db文件弹出一个框，输入刚才7位的钥匙，就能顺利打开了微信数据库了<img src="https://pic2.zhimg.com/50/9b191da1b96b92463e780ca12d131f52_hd.jpg" data-rawwidth="304" data-rawheight="122" class="content_image" width="304">打开效果如下<img src="https://pic2.zhimg.com/50/564b39d6d19cff390e61b4d73e164d05_hd.jpg" data-rawwidth="925" data-rawheight="495" class="origin_image zh-lightbox-thumb" width="925" data-original="https://pic2.zhimg.com/564b39d6d19cff390e61b4d73e164d05_r.jpg">

5.选择导出成Excel即可
6.找到对应ID的聊天记录并且导入到另一个Excel表中
##### 二.处理需要的照片文件
将如下的照片文件抠出主体
![](https://github.com/h1997l1997/Analysis-of-Wechat-history-/blob/master/example/HER_8731.jpg)
变成下面的样子，保存为png文件
![](https://github.com/h1997l1997/Analysis-of-Wechat-history-/blob/master/example/1.png)
保存名为1.png
##### 二.运行代码
导出的聊天记录文件表重命名为message.xlsx即可

### 代码流程
> 处理message.xlsx将有效的聊天内容存入test.txt文件内

> 读取test文件的聊天记录进行词频分析

> 根据设定背景绘制词云图


### 运行结果式样
![](https://github.com/h1997l1997/Analysis-of-Wechat-history-/blob/master/example/1_x.png)
![](https://github.com/h1997l1997/Analysis-of-Wechat-history-/blob/master/example/2_x.png)
![](https://github.com/h1997l1997/Analysis-of-Wechat-history-/blob/master/example/4_x.png)
![](https://github.com/h1997l1997/Analysis-of-Wechat-history-/blob/master/example/5_x.png)
![](https://github.com/h1997l1997/Analysis-of-Wechat-history-/blob/master/example/show_Chinese.png)

#### 欢迎关注本项目并且关注我的Github账户
