```sh
# mac 取消密码限制
pwpolicy -clearaccountpolicies
# 修改密码
passwd

# 从任何来源安装软件
sudo spctl --master-disable

# homebrew 太慢
brew install 会先执行 brew update, 可使用 ctrl-c 跳过
```

## mark

- 如果使用 docker, 推荐 16g+
- 触控板
    - 使用轻点取代按下: 设置-触控板-轻点来点按
    - 三指拖拽: 设置-辅助-鼠标和触控板-触控板选项
- 快捷键
    - touchbar + fn
- 软件
    - [搜狗输入法](https://pinyin.sogou.com/mac/): 英文输入 语音输入
        - 自定义短语: https://gist.github.com/tualatrix/5022892
    - Chrome
        - 推展推荐: vimium
        - 其他
            - extension
                - 谷歌访问助手(http://www.ggfwzs.com/)
            - 打开多线程下载: chrome://flags -> 搜索 download
            - password 需要配合使用 iCloud
    - alfred(效率神器): https://xclient.info/s/alfred.html
        - 设置快捷键, 替换 spotlight: 设置-快捷键-spotlight-取消所有; Alfred设置快捷键为 cmd+空格
        - 切换应用
        - 打开网页收藏夹: 设置-feature-网页收藏夹
        - workflow: yd(有道翻译) 计算器 自定义搜索(bm 百度地图)
    - [things](https://www.jianshu.com/p/4de1ffd3d6d9): 双手不离开键盘完成 todo list 管理
        - datetime: https://support.culturedcode.com/customer/en/portal/articles/2803579-using-dates-and-time-in-things
        - keyboard for mac: https://support.culturedcode.com/customer/en/portal/articles/2785159-keyboard-shortcuts-for-mac
        - quick find: https://support.culturedcode.com/customer/portal/articles/2803584#navigate-with-quick-find
    - nimble commander: 类似 total commander 的文件管理工具
    - vscode: https://code.visualstudio.com/docs/?dv=osx
        - 快捷键
            - Cmd-S-p: 打开 command 面板
        - 添加 code 命令到 PATH 中, 方便打开文件: command 面板 -> 输入 path
        - 自动保存: command 面板 -> autosave
        - 添加 vim: command 面板 -> keymaps -> vim
    - magnet: 窗口管理工具
        - 只保留常用: 窗口调整到左右 / 窗口到不同显示器 / 窗口居中或最大化
        - 切换显示器, 窗口还是会保持
    - jietu 截图工具: https://jietu.qq.com/
        - 配置快捷键, 只保留截图快捷键, 关闭其他应用(微信/qq/企业微信/钉钉)的截图快捷键
    - homebrew: mac 包管理工具
        - 常用工具: git curl tree
        - fish: 超好用的shell
            - fish_config(~/.config/fish/fish_config)
        - 其他工具
            - ag: 高效内容查找, 比 grep/awk 更快的递归搜索文档
            - htop: 代替 top
            - jq: 格式化显示 json
        - brew cask 常用工具: iterm2 google-chrome firefox vscode
    - iterm2 + fishshell
        - git 状态
        - 代码自动补全
        - 为重复工作添加小脚本
    - github 客户端: https://desktop.github.com/
        - 方便查看修改 -> 写完代码一定要自己 review, 自己自测
    - docker - 搞定开发环境
        - docker desktop + aliyun下载文件 + docker 中文网源
        - docker desktop
        - docker-compose
    - vscode - 文本编辑
    - phpstorm - IDE
        - 提示
        - 补全
        - 重构
    - datagrip - 数据库管理工具
        - 自动补全
        - 快速切连接
        - 快速打开表
        - 快速查看DDL
    - charles [视频教程](https://www.cnblogs.com/weimjsam/p/5841816.html)
        - 无法抓包 -> 白名单/代理冲突
        - 无法抓localhost: https://www.charlesproxy.com/documentation/faqs/localhost-traffic-doesnt-appear-in-charles/
    - 迅雷
    - [imageopti](https://imageoptim.com/mac) 无损优化图片
    - [picgo](https://molunerfinn.com/PicGo/) + 七牛云: 图片上传工具
    - quicktime 视频剪切: cmd-t

```bash
# allow app form anywhere
sudo spctl --master-disable

# SIP(system integrity protection, rootless)
csrutil disable

# 使用简单密码
pwpolicy -clearaccountpolicies
passwd # 修改密码

# 删除默认输入法
cd ~/Library/Preferences
cp com.apple.HIToolbox.plist com.apple.HIToolbox.plist.bak
sudo open com.apple.HIToolbox.plist # 关闭SIP -> 切换到默认输入法, 才能保存 -> 安装xcode, 也可以 xed com.apple.HIToolbox.plist -> 重启

# 干掉 dock
defaults write com.apple.dock autohide-delay -int 100 # 100s, 配合自动隐藏
killall Dock

# 七牛图片高级处理: https://developer.qiniu.com/dora/manual/1270/the-advanced-treatment-of-images-imagemogr2
?imageMogr2/auto-orient/thumbnail/500x500 # 自动旋转; 等比限宽+高缩放
?imageMogr2/rotate/-90 # 旋转

# dns
networksetup -listallnetworkservices
networksetup -setdnsservers Wi-Fi 180.76.76.76 223.5.5.5 # baidu/ali dns
networksetup -getdnsservers Wi-Fi
dscacheutil -flushcache
```

## alfred

alfred的确是神器, 需要好好提提:

- 切应用: 常用应用可以「调教」到输入一个字母解决
- 搜索 文件
- 搜索 chrome 书签
- 设置 百度/百度地图 搜索
- 设置 微云 同步配置

[Alfred workflow](https://www.jianshu.com/p/0e78168da7ab)
[workflow - gtihub](https://github.com/gharlan/alfred-github-workflow): `gh > help` 查看帮助

## iterm2

switch: window(O-Cmd)-tab(cmd)-pane(O, 需要在设置中开启, Cmd-S-d 水平拆分 tab 为上下 2 个 pane)
mouseless copy C-f-tab
Autocomplete C-;
Paste History C-S-h
Full Screen C-enter
Window Arrangements: 保存常用TAB布局
Shell Integration/Utilities https://iterm2.com/documentation-shell-integration.html
Password Manager
show timestamp
open quickly
find cursor C-/
iterm2 粘贴时有多余字符 0~ 1~: `printf '\e[?2004l'`
copy mode: cmd-S-c(进入) -> C-v(选中模式) jkhl(移动) y(复制)
使用ubuntu主题: Preferences(cmd+,)-Profiles-default-colors-(Color Presets...)下拉中选择ubuntu
可以点击Visit Online Gallery下载颜色主题

## pdf 工具
- clear view: 看
- pdf element(万兴pdf): 去水印(watermark)
- smallpdf.com: unlock
- pdf plus: 合并
- pdf squeeze: 压缩
- pdf expert: 编辑(没使用)

## reference

- [tech| 我的开发环境 & 效率工具](https://www.jianshu.com/p/1fea03604c19)
- [tech| 开发环境之 IDE](https://www.jianshu.com/p/f9e38793a0d3)
- [tech| 开发环境之window](https://www.jianshu.com/p/3d3f4fd3d568): 换 mac 

---

- [还在用 Win？教你从零把 Mac 打造成开发利器](https://mp.weixin.qq.com/s/qRzpNHZSL6hnZNwUnoaO1g)
- [mac 按键标识](https://blog.csdn.net/HaoDaWang/article/details/78731098)
- [mac 软件下载](https://xclient.info)
- [mac 找到快捷键](https://sspai.com/post/45338)
- mac 常用快捷键: https://support.apple.com/zh-cn/HT201236
- 外接显示器: http://tieba.baidu.com/p/5007071765
- 生产力工具链: https://github.com/Louiszhai/tool

## mac PHP环境一键配置

```sh
# homebrew https://brew.sh/
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
# 安装 homebrew 慢, 先下载 install 文件, 然后替换为 https://gitee.com/mirrors/homebrew

# homebrew 加速源: https://mirror.tuna.tsinghua.edu.cn/help/homebrew/
git -C "$(brew --repo)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git
brew tap homebrew/core
git -C "$(brew --repo homebrew/core)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git
brew tap homebrew/cask
git -C "$(brew --repo homebrew/cask)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask.git
brew update
# 复原
# git -C "$(brew --repo)" remote set-url origin https://github.com/Homebrew/brew.git
# git -C "$(brew --repo homebrew/core)" remote set-url origin https://github.com/Homebrew/homebrew-core.git
# git -C "$(brew --repo homebrew/cask)" remote set-url origin https://github.com/Homebrew/homebrew-cask.git
# brew update

# homebrew-bottles
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles' >> ~/.bash_profile
source ~/.bash_profile

# iterm2
brew cask install iterm2

# vim: 可以命令行使用 code 命令, 使用 vscode 编辑文件
# brew install vim

# fish shell: 推荐使用
brew install fish
# sudo echo '/usr/local/bin/fish' >> /etc/shells
# chsh -> 切换默认shell
# fish_config -> 配置 fish
# fish 配置目录: ~/.config/fish

# php: 项目中目前统一使用 7.2
# 踩到的坑: 本地 7.3 更新 composer 后, 有的包更新后强制要求使用 7.3, 导致其他环境 composer i 失败
brew install php@7.2
# 安装后注意根据提示添加 PATH
# composer: https://developer.aliyun.com/composer
composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/
# pecl: http://pecl.php.net/
# 可以在 pecl 上下载好包后直接安装, 避免重复网络请求
# swoole
# 确保环境变量里能找到 openssl 的编译库
pecl install swoole-4.4.13.tgz
# 使用 `php --ini` 查找 php.ini 文件位置, 编辑添加 `swoole.use_shortname = 0`, 使用 `php --ri swoole` 确认是否生效
pecl install redis-5.1.1.tgz
pecl install mongodb-1.6.1.tgz
# protobuf
brew install protobuf
pecl install protobuf-3.11.1.tgz
# kafka
brew install librdkafka
pecl install rdkafka-4.0.0.tgz
# zookeeper
brew install zookeeper
pecl install zookeeper-0.6.4.tgz
```