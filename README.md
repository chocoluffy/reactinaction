##Some important details need to be writed down##

## update .gitignore file to avoid uploading some unnecessary files

```
curl https://raw.githubusercontent.com/github/gitignore/master/Node.gitignore > .gitignore
```

## NPM init

so that’s how to initiate a NPM project. The most important part is to have  a `package.json` that includes the dependency node modules. and by using `nom init` we can have such project created. 

## install BrowserSync

when we have such node installed, we can allow the view to sync to Browser. 
The way we install this package is to use
```
npm install browser-sync@2.9.3 —save -d
```
`—save` is for to append the module browser-sync to `package.json`
`-d` is to let npm to output more details.

## some useful commands

`find node_modules` to see the module installed in local project
`git diff` to see the difference between current project structure with the committed one. and we can see that we add this module into the `package.json` file correctly.
`npm ls` to see the npm module dependency

## 当NPM包为一个命令行工具 Set path

假如某个 NPM 包是一个命令行工具，可执行文件会被安装在 node_modules/.bin 这个目录

`ls node_modules/.bin` 执行命令时我们可以加上 --help 选项来查看帮助信息.

**PATH 环境变量**
为了可以用 browser-sync 来执行命令，而不是完整路径 ./node_modules/.bin/browser-sync，我们需要修改 PATH 环境变量。这样系统才能找到 browser-sync 这个命令。

首先，让我们看看 PATH 的当前值：

```
$ echo $PATH
Users/yushunzhe/.rvm/gems/ruby-2.3.0/bin:/Users/yushunzhe/.rvm/gems/ruby-2.3.0@global/bin:/Users/yushunzhe/.rvm/rubies/ruby-2.3.0/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/opt/X11/bin:/usr/local/go/bin:/usr/texbin:/Users/yushunzhe/.rvm/gems/ruby-2.2.1/bin:/Users/yushunzhe/.rvm/gems/ruby-2.2.1@global/bin:/Users/yushunzhe/.rvm/rubies/ruby-2.2.1/bin:/opt/local/bin:/opt/local/sbin:/Library/Frameworks/Python.framework/Versions/3.4/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/opt/X11/bin:/usr/local/go/bin:/usr/texbin:/Users/yushunzhe/.rvm/bin
```
为了让系统在 ./node_modules/.bin 中查找 browser-sync，我们需要把那个目录添加到 PATH 环境变量中：
`export PATH=$PATH:./node_modules/.bin`

如果希望长时间的把这个命令在命令行中直接运行启动， 需要把上面那个命令放在`~/.zshrc`中， 使用`sublime ~/.zshrc`打开。

然后用下面这个命令运行服务器：
```
browser-sync start --server --files=index.html
```

## Makefile
makefile的作用， 其实就是常见一些常用的命令， 然后获得一个shortcur.

一个 Makefile “规则” 通常会创建作为输出的文件。.PHONY: server 是说 server 是一个任务，并不会输出文件。

reference to [this post](http://www.sitepoint.com/using-gnu-make-front-end-development-build-tool/)

##  补充CSS特性
 
- `@import ` 把多个CSS文件汇集成包
- 使用`autoprefix`为新的CSS属性生成前缀

```
mkdir -p bundle
```	
参数-p的意思是后面可以跟一个路径， 如果路径上的文件夹不存在， 那么mkdir也会创建那些文件夹。

## normalize.css

浏览器行为表现彼此略有不同。normalize.css 使浏览器的行为更相似。举个例子，你以前知道在 IE 8/9/10 中，如果 img 在一个 a 元素内，它会有边框这件事吗？

the difference between —save-dev and —save:

devDependencies are for the development-related scripts, e.g. unit testing, packaging scripts, documentation generation, etc.

dependencies are required for production use, and assumed required for dev as well.























