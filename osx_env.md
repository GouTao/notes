## Mac OS 开发环境配置

### 用brew安装并管理软件

[官网](http://brew.sh/index_zh-cn.html)  

在终端执行:  

```ruby
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

> os x系统自带ruby。上边的脚本会把Homebrew安装到 `/usr/local` 下, 所以用 `brew install`时不用加 `sudo`。Homebrew 会将套件安装到独立目录，并将文件软链接至 /usr/local 。  

**[coding](https://coding.net/u/cocodingding/pp/84498)的 brew 国内源加速**  
```shell
$ cd /usr/local && git remote set-url origin https://git.coding.net/homebrew/homebrew.git
$ cd $home && brew update
```

#### 常用命令

1. `brew install xxx` : 安装 (注: 建议先执行 `brew update`)
1. `brew uninstall xxx` : 卸载
1. `brew search /git*/` : 用正则表达式搜索软件
1. `brew list` : 列出已安装软件
1. `brew update` : 更新brew
1. `brew upgrade xxx` : 更新某个软件 (注: 需先执行brew update更新brewjj)
1. `brew home` : 用浏览器打开brew的官方网站
1. `brew info` : 显示软件信息
1. `brew deps xxx` : 显示包依赖
1. `brew outdated` : 查看过时的库
1. `brew cleanup` : 清理调过期的库和应用

> 建议在用brew安装软件之前先执行 `brew update`  

### MySQL

**安装**  

`brew install mysql`

**启动/停止服务**

```shell
mysql.server start
mysql.server stop
```

> 运行 `brew info mysql`, 最后有一段话提示了如何开机自启mysql，或者临时启动:    

```shell
# To have launchd start mysql at login:
  ln -sfv /usr/local/opt/mysql/*.plist ~/Library/LaunchAgents
# Then to load mysql now:
  launchctl load ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist
# Or, if you don't want/need launchctl, you can just run:
  mysql.server start
```

### MongoDB

**安装**  

`brew install mongodb`  

> `brew info mongodb` 同样也可以查看如何设置mongodb开机启动方式:

```shell
o have launchd start mongodb at login:
  ln -sfv /usr/local/opt/mongodb/*.plist ~/Library/LaunchAgents
Then to load mongodb now:
  launchctl load ~/Library/LaunchAgents/homebrew.mxcl.mongodb.plist
Or, if you don't want/need launchctl, you can just run:
  mongod --config /usr/local/etc/mongod.conf
```

**运行 `mongod` 报错:**  

> I STORAGE  [initandlisten] exception in initAndListen: 98 Unable to create/open lock file: /data/db/mongod.lock errno:13 Permission denied Is a mongod instance already running?, terminating  

> 解决:  
```shell
sudo chown -R `id -u` /data/db
```

##### 连接到MongoDB

> [MongoDB 快速入门](http://docs.mongoing.com/manual-zh/tutorial/getting-started.html)  

 - `mongod`: 启动MongoDB服务  
 - `mongo`: 连接到MongoDB 

> 默认情况下 `mongo` 程序会自动尝试去连接到本机localhost的 `27017` 端口。 若要连接到一个不同的服务器或者不同端口，使用参数 `--host` 。

> mongo 程序启动时会默认选定 test 数据库。切换数据库: `use mydb`  

- `show db/databases`: 列出所有数据库
- `db`: 当前数据库

### Redis

**安装**  

`brew install redis`  

**启动/停止/查看服务状态**  

手动启动服务:  

`redis-server /usr/local/etc/redis.conf`  
>  启动后可以看到redis启动界面及ip地址

```shell
brew services list | grep redis
brew services start redis
brew services stop redis
```

> 用这种方式启动之后会显示 `started hugo /Users/hugo/Library/LaunchAgents/homebrew.mxcl.redis.plist`, 但是看不到redis的ip地址, 需要运行 `ps aux | grep redis` 查看。


### 参考 

- [Mac 开发配置手册](https://aaaaaashu.gitbooks.io/mac-dev-setup/content/)
- [dev-setup](https://github.com/donnemartin/dev-setup)
