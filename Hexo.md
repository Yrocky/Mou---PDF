
Mac上搭建hexo极简指南
=====

安装`nvm`(node.js的版本管理工具）
> $ wget -qO- https://raw.github.com/creationix/nvm/master/install.sh | sh


安装`node.js`(通过nvm安装)
添加如下内容到.zshrc配置文件
> $ nvm install 0.10



安装`hexo`（通过npm安装）
> $ npm install -g hexo


创建hexo文件夹，并安装hexo相关组件
> $ hexo init hexo

> $ cd hexo

> $ npm install



本地查看
输入如下命令后，打开浏览器，并输入localhost:4000来查看
> $ hexo g

> $ hexo s


+ 注册github账号
+ 创建github账号同名repository
+ eg:github账号名位dorayox，则创建dorayox.github.io
+ 部署到github上

如下所示编辑_config.yml

> deploy:
 
> type: github

> repository: git@github.com:dorayox/dorayox.github.io.git

> branch: master



输入如下命令，完成到github得部署，之后打开浏览器并输入dorayox.github.io来查看
> $ hexo g
> 
> $ hexo d





