> http://brew.sh/

- 安装

```sh
# 理想情况
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

# 加速
curl -O https://raw.githubusercontent.com/Homebrew/install/master/install.sh
# 修改 BREW_REPO 为 https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git 后执行 install.sh
```

- fishshell 下 brew 加速

```sh
# brew
set -gx HOMEBREW_BOTTLE_DOMAIN https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles
function brew_ori
    git -C (brew --repo) remote set-url origin https://github.com/homebrew/brew.git
    git -C (brew --repo homebrew/core) remote set-url origin https://github.com/homebrew/homebrew-core.git
    set -e HOMEBREW_BOTTLE_DOMAIN https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles
    git -C (brew --repo homebrew/cask) remote set-url origin https://github.com/homebrew/homebrew-cask.git
end
function brew_aliyun
    git -C (brew --repo) remote set-url origin https://mirrors.aliyun.com/homebrew/brew.git
    git -C (brew --repo homebrew/core) remote set-url origin https://mirrors.aliyun.com/homebrew/homebrew-core.git
    set -gx HOMEBREW_BOTTLE_DOMAIN https://mirrors.aliyun.com/homebrew/homebrew-bottles
end
function brew_thu
    # https://mirrors.tuna.tsinghua.edu.cn/help/homebrew/
    git -C (brew --repo) remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git
    git -C (brew --repo homebrew/core) remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git
    set -gx HOMEBREW_BOTTLE_DOMAIN https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles
    git -C (brew --repo homebrew/cask) remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask.git
end
```

- brew 常用操作

```sh
brew search xxx
brew install xxx
brew info xxx

# brew cask
brew cask install xxx

# 其他
brew --repo
brew --repo brew/core
```

- brew install 会先执行 brew update, 可使用 ctrl-c 跳过