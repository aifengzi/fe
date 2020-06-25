## version
version是版本（遵守“大版本.次要版本.小版本”的格式）

## dependencies, devDependencies
dependencies是项目运行时所依赖的模块；devDependencies是项目开发时所依赖的模块。

- 指定版本：比如1.3.2，遵循大版本.次要版本.小版本的格式规定。安装时只安装指定的版本；
- 波浪号 + 指定版本：比如~1.3.2，表示安装1.3.X的最新版本(不低于1.3.2，但是不安装1.4.X，也就是说安装时不改变大版本和次要版本)；
- 插入号 + 指定版本：比如^1.3.2，表示安装1.X.X的最新版本(不低于1.3.2，但是不安装2.X.X，也就是说安装时不改变大版本)如果大版本是0，则插入号的行为和波浪号一致，这是因为此时处于开发阶段。即使次要版本号的变动，也可能打开程序的不兼容；
- latest：安装最新版本；

## --save, --save-dev
`--save`参数表示将该模块写入dependencies；
`--save-dev`参数表示将该模块写入devDependencies；

## peerDependencies
`用来供插件指定其所需要的主工具的版本`
[参考](https://javascript.ruanyifeng.com/nodejs/packagejson.html)
[参考](https://www.cnblogs.com/wonyun/p/9692476.html)

## bin
bin字段用来指定各个内部命令对应的可执行文件的位置。

```json
"bin": {
  "someTool": "./bin/someTool.js"
}
```

挡在node窗口中执行someTool命令时，npm会寻找这个文件，并且在node_modules/.bin/目录下建立符号链接。
`由于node_modules/.bin/目录会在运行时加入系统的PATH变量`，因此在运行npm时，就可以不带路径，直接通过命令来调用这些脚本。


## config
config字段用于添加命令行的环境变量。

```json
{
  "name" : "foo",
  "config" : { "port" : "8080" },
  "scripts" : { "start" : "node server.js" }
}
```

在server.js脚本就可以引用config字段中的值。
```javascript
http
  .createServer(...)
  .listen(process.env.npm_package_config_port)
```

用户也可以变修改这个值。
```javascript
npm config set foo:port 80
```

## npm插件

## npm依赖管理
