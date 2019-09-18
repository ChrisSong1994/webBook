### npm 常用命令行总结


#### npm是什么
> NPM的全称是Node Package Manager，是随同NodeJS一起安装的包管理和分发工具，它很方便让JavaScript开发者下载、安装、上传以及管理已经安装的包。

#### npm install安装模块
- 基础语法
``` javascript
npm install (with no args, in package dir)
npm install [<@scope>/]<name>
npm install [<@scope>/]<name>@<tag>
npm install [<@scope>/]<name>@<version>
npm install [<@scope>/]<name>@<version range>
npm install <tarball file>
npm install <tarball url>
npm install <folder>

alias: npm i
common options: [-S|--save|-D|--save-dev|-O|--save-optional] [-E|--save-exact] [--dry-run]
```
安装包，默认会安装最新的版本

#### npm uninstall 卸载模块 
- 基础语法
``` javascript
npm uninstall [<@scope>/]<pkg>[@<version>]... [-S|--save|-D|--save-dev|-O|--save-optional]

aliases: remove, rm, r, un, unlink
```

#### npm update 更新模块
- 基础语法
``` javascript
npm update [-g] [<pkg>...]
```


#### npm outdated 检查模块是否已经过时
- 基础语法
``` javascript
npm outdated [[<@scope>/]<pkg> ...]
```

#### npm ls 查看安装的模块
- 基础语法
``` javascript
npm ls [[<@scope>/]<pkg> ...]
aliases: list, la, ll
```
- 查看全局安装的模块及依赖 
```
npm ls -g
```
 
 #### npm init 在项目中引导创建一个package.json文件
安装包的信息可保持到项目的package.json文件中，以便后续的其它的项目开发或者他人合作使用，也说package.json在项目中是必不可少的
- 基础语法
``` javascript
npm init [-f|--force|-y|--yes]
```

#### npm help 查看某条命令的详细帮助 
- 基础语法
``` javascript
npm help <term> [<terms..>]
```
例如输入npm help install，系统在默认的浏览器或者默认的编辑器中打开本地nodejs安装包的文件/nodejs/node_modules/npm/html/doc/cli/npm-install.html
``` javascript
npm help install
```



#### npm root 查看包的安装路径
输出 node_modules的路径
``` javascript
npm root [-g]
```

#### npm config 管理npm的配置路径
- 基础语法
``` javascript
npm config set <key> <value> [-g|--global]
npm config get <key>
npm config delete <key>
npm config list
npm config edit
npm get <key>
npm set <key> <value> [-g|--global]
```
经常用于设置镜像
```
npm config set registry="http://r.cnpmjs.org"
```
如安装淘宝镜像
```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

#### npm cache 管理模块的缓存
- 基础语法
``` javascript
npm cache add <tarball file>
npm cache add <folder>
npm cache add <tarball url>
npm cache add <name>@<version>
npm cache ls [<path>]
npm cache clean [<path>]
```
最常用命令清除npm本地缓存
```
npm cache clean
```



#### npm start 启动模块
- 基础语法
``` javascript
npm start [-- <args>]
```
该命令写在package.json文件scripts的start字段中，可以自定义命令来配置一个服务器环境和安装一系列的必要程序，如
``` javascript
"scripts": {
    "start": "gulp -ws"
}
```
此时在cmd中输入npm start命令相当于执行gulpfile.js文件自定义的watch和server命令。
如果package.json文件没有设置start，则将直接启动node server.js


#### npm stop 停止模块
- 基础语法
``` javascript
npm stop [-- <args>]
```


#### npm restart 重新启动模块
- 基础语法
``` javascript
npm restart [-- <args>]
```

#### npm test 测试模块
- 基础语法
``` javascript
npm test [-- <args>]
npm tst [-- <args>]
```
该命令写在package.json文件scripts的test字段中，可以自定义该命令来执行一些操作，如
``` javascript
"scripts": {
    "test": "gulp release"
},
```
此时在cmd中输入npm test命令相当于执行gulpfile.js文件自定义的release命令。


#### npm version 查看模块版本
- 基础语法
``` javascript
npm version [<newversion> | major | minor | patch | premajor | preminor | prepatch | prerelease | from-git]

'npm [-v | --version]' to print npm version
'npm view <pkg> version' to view a package's published version
'npm ls' to inspect current package/dependency versions
```
查看模块的版本
``` javascript
npm version
```
例：
``` javascript
{ store_eve: '0.1.0',
  npm: '6.9.0',
  ares: '1.10.1-DEV',
  cldr: '32.0',
  http_parser: '2.8.0',
  icu: '60.1',
  modules: '57',
  nghttp2: '1.25.0',
  node: '8.11.1',
  openssl: '1.0.2o',
  tz: '2017c',
  unicode: '10.0',
  uv: '1.19.1',
  v8: '6.2.414.50',
  zlib: '1.2.11' }
```



#### npm view 查看模块的注册信息
- 基础语法
``` javascript
npm view [<@scope>/]<name>[@<version>] [<field>[.<subfield>]...]

aliases: info, show, v
```
查看模块的依赖关系
``` javascript 
npm view gulp dependencies
```
查看模块的源文件地址
``` javascript 
npm view gulp repository.url
```
查看模块的贡献者，包含邮箱地址
``` javascript 
npm view npm contributors
```



#### npm adduser 用户登录
- 基础语法
``` javascript
npm adduser [--registry=url] [--scope=@orgname] [--always-auth]
```
发布模板到npm社区前需要先登录，然后再进入发布的操作


#### npm publish 发布模块
- 基础语法
``` javascript
npm publish [<tarball>|<folder>] [--tag <tag>] [--access <public|restricted>]

Publishes '.' if no argument supplied
Sets tag 'latest' if no --tag specified
```

#### npm access 在发布的包上设置访问级别
- 基础语法
``` javascript
npm access public [<package>]
npm access restricted [<package>]
npm access grant <read-only|read-write> <scope:team> [<package>]
npm access revoke <scope:team> [<package>]
npm access ls-packages [<user>|<scope>|<scope:team>]
npm access ls-collaborators [<package> [<user>]]
npm access edit [<package>]
```