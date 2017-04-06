## 问&答

### 如何安装脚本？

使用脚本前必须安装扩展，各浏览器对应的扩展如下：

1. Firefox浏览器：[Greasemonkey](https://addons.mozilla.org/zh-CN/firefox/addon/greasemonkey/)
2. 傲游浏览器：[Violentmonkey](http://extension.maxthon.com/detail/index.php?view_id=1680)
3. Chrome浏览器：[Tampermonkey](https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo)
    * 访问不了[Chrome 网上应用店](https://chrome.google.com/webstore/category/extensions)的同鞋可以到下面的地址下载crx文件。下载下来的crx文件可能不能直接安装，需要手动拖到扩展管理界面（一般为`chrome://extensions/`）中，应该就能安装成功了：
        * [Tampermonkey各版本百度网盘](http://pan.baidu.com/s/1nuCc4Al)
        * [常用Crx离线安装包下载](https://yurl.sinaapp.com/crx2.php)
    * 国内的360极速浏览器、猎豹浏览器等其实上就是Chrome加个壳，装Tampermonkey就行了
    * 搜狗高速浏览器：[Tampermonkey Legacy](http://ie.sogou.com/app/app_4326.html)

### 安装脚本后打开番剧视频的播放页面变卡？

1. 因为该脚本是通过拦截获取视频地址的请求，从另一个服务器获取真实视频地址的方式实现的。获取真实视频地址的操作是在主线程中进行的，所以必然会卡一下。。。不过大家请放心，在不需要替换视频地址的页面是不会去进行这些操作的。

### 安装脚本后无效？

0. 确定你使用的播放器是HTML5版的。Flash版请在播放器界面的右上角切换成HTML5版。
1. 确定你打开的页面的域名是`bangumi.bilibili.com`开头的，当前该脚本只在这个域名下开启了。以京吹为例，在[这个页面](http://bangumi.bilibili.com/anime/5551/)下点开的链接就是`bangumi.bilibili.com`域名下的。  
2. 如果还是无效的话，大概是因为获取真实地址的请求失败了。。。我服务器太渣的原因。。一般多刷新几下应该就可以了。。。  
3. 如果依然无效，可能确实是这个脚本的问题了，请反馈给我：[解除B站区域限制 - 反馈](https://greasyfork.org/zh-CN/scripts/25718-%E8%A7%A3%E9%99%A4b%E7%AB%99%E5%8C%BA%E5%9F%9F%E9%99%90%E5%88%B6/feedback)

### 看不了1080P画质？

1. 确定你是B站的[大会员](http://big.bilibili.com/site/big.html)
2. 确定当前视频拥有1080P画质的版本
3. 确定你登录了[我的反向代理服务器](http://biliplus.ipcjsdev.tk/login)；注意，当前只支持“使用bilibili账号密码进行登录”

### https下无效？
B站当前是支持https的，但默认还是用http。因为我的反向代理服务器还没有支持https的原因，获取真实播放地址的网络请求默认会被Chrome、Firefox阻止。。

- Chrome永久解除阻止的方法是，启动时添加参数`--allow-running-insecure-content`（**不推荐**）
- Firefox临时解除阻止的方法是，点击地址栏左侧的锁状图标，选择`暂时解除保护`

### 大会员账号被B站永封了？<img src="http://bbs.saraba1st.com/2b/static/image/smiley/nq/010.gif" alt="懵逼"/>

0. 注册并登录一个小号
1. 安装并修改[脚本](https://greasyfork.org/zh-CN/scripts/25718-%E8%A7%A3%E9%99%A4b%E7%AB%99%E5%8C%BA%E5%9F%9F%E9%99%90%E5%88%B6)中的变量`i_am_a_big_member_who_is_permanently_banned`为`true`
2. 在[我的反向代理服务器](http://biliplus.ipcjsdev.tk/login)中使用账号密码登录被永封的大会员账号
3. 就可以用小号看1080P了<img src="http://bbs.saraba1st.com/2b/static/image/smiley/nq/001.gif" alt="扭曲"/>

### 想自定义服务器？

1. 打开浏览器的`开发者工具`（快捷键一般为`F12`）
2. 在`控制台/Console`中执行如下代码，将服务器地址存到cookie中（其中`https://www.your_server.com`替换成你自己的服务器）：
```javascript
    document.cookie=`bangumi_aera_limit_hack_server=https://www.your_server.com; domain=.bilibili.com; path=/; expires=${new Date("2020-01-01").toUTCString()}`; 
```

### 想要帮忙维护？

1. 源码仓库：[ipcjs/bilibili-helper at user.js](https://github.com/ipcjs/bilibili-helper/tree/user.js)