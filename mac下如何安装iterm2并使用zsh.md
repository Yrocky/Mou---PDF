# Mac下如何安装iTerm2并使用zsh

## iTerm2
1. 下载iTerm2
2. 把iTerm2移动到应用程序文件夹中
3. 双击iTerm2来启动iterm2，并在dock中保留


## zsh
1. 下载oh-my-zsh
2. mv oh-my-zsh ~/.oh-my-zsh
3. 下载dotfiles (git clone http://github.com/dorayo/dotfiles.git)
4. mv dotfiles ~/dotfiles
5. cd ~/dotfiles
6. ./install.sh
7. chsh -s /bin/zsh
8. 关闭并重新打开iTerm2