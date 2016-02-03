## 用Ghost搭建博客 

github: [https://github.com/TryGhost/Ghost](https://github.com/TryGhost/Ghost)  ([中文版](https://github.com/ghostchina/Ghost-zh))

## 安装
- git clone https://github.com/TryGhost/Ghost.git
- 切换到stable分支（当前最新稳定版）
- 配置mysql数据库（默认使用sqllite3数据库）
  - `cp config.example.js config.js`
  - copy testing-mysql 配置到 production（生产环境，提供域名）或development（默认，开发环境，localhost，测试数据库）并修改，development注意端口一致

  
## 启动/配置
- npm install
- grunt init (安装bower依赖包并执行一些构建任务, 我本地执行时报[Fatal error: Cannot read property 'headers' of undefined](https://github.com/TryGhost/Ghost/issues/6276)，原因不明，改用`grunt`)
- npm start
- 会提示`Url configured as: http://localhost:2368`，访问即可
- 访问 /ghost 页面进入台，按提示初始化一个用户（博客所有者），中间可邀请团队成员，也可跳过，以后再邀请

## 技术选型
1. ES6
1. node.js (v1.10.x)
2. sqllite3
3. Ember.js
4. Handlebars.js
5. nodemailer

## TODO

- 邮件配置
- [更换/自定义主题](http://docs.ghost.org/zh/themes/)   
	http://marketplace.ghost.org/ (Ghost主题集市)  
  - https://github.com/onevcat/vno （个人博客主题，推荐）  
  - https://github.com/blinkfox/ghost-matery
  - https://github.com/oswaldoacauan/ghostium
  - https://github.com/ghostchina/Casper-zh   
  - https://github.com/ghostchina/Roon-zh
  	
- 排版
  - UI  
    - [人人小站](http://zhan.renren.com/home?checked=true)   
    - [淘宝UED](http://ued.taobao.org/blog/)
  - 文字  
    - [typeisbeautiful.com](http://www.typeisbeautiful.com/) - 中文文字排版之美  
  	- [Amaze UI](amazeui.org)
  	
- 分页导航
- 添加统计代码（百度或CNZZ）
- 添加highlight.js代码语法高亮
- 评论系统（多说或Disqus）
- 字体排版优化
- 标签云
- 自定义错误页面
- 在首页展示文章的特色图
- pm2

### 性能优化
1. 替换Google Fonts（googleapis 替换成 useso）
1. CDN加速
1. 用Nginx做反向代理

## 参考
- http://www.ghostchina.com/
- https://www.bokeyy.com/post/ghost-install-in-vps-solution-in-china.html
- http://support.ghost.org/supported-node-versions/
- [「搭建Ghost博客」经典教程](http://segmentfault.com/a/1190000002947497)
- [如何搭建一个Ghost平台的博客？](https://www.zhihu.com/question/22755373)





