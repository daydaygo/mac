现代 php 框架浅析:

- 核心: container 容器
- 应用 & 应用生命周期管理: app 应用

# container 容器

现代 php 框架的核心其实都是一致的: container 容器(和 DI 依赖注入, IoC 控制反转 是同一语境), 解决的问题如下:

```php
// 如果类 A 的实例 a 需要使用到类 B 的实例 b
$a->b = new B();

// 如果有 container
$a->b = $container->get(B::class);

// 不仅仅是 A 依赖 B, 其他依赖的地方, 都可以直接用, 比如类 C 的实例 c
$c->b = $container->get(B::class);
```

# app 应用(服务)

用 **生命周期** 来理解 app 会比较好理解

- 入口文件
  - ini
  - 常量
  - composer autoload
  - container
  - app
- app 执行流程
  - command
  - server
    - mvc
    - route -> middleware -> controller -> service / model / view
  - 常用组件
    - config
    - log
    - redis mysql

# php 基础

- PHP 的配置
  - 查看: `php -i |grep xxx'
  - 设置
    - 可以使用 `php --ini` 查看配置文件, 通过修改配置文件设置 
    - 可以在代码中用 `ini_set()` 进行配置
- composer
  - 我想用别人的代码, 怎么用
    - 别人的代码 package: 
      - 设置自动加载: composer.json -> autoload -> ps-4: namespace(命名空间) <=> path(文件路径)
      - 设置名字: composer.json -> name
    - 依赖管理
      - composer.json -> require -> package name
      - composer install/require
        - package -> vendor 目录
        - 生成好 `vendor/autoload.php`
      - 入口添加自动加载文件 `require BASE_PATH . '/vendor/autoload.php';`

# 网络基础

- tcp/ip 4层
- server / client
- http 协议: url path method header body request/response

# co 协程基础

- 进程 线程 协程
  - 进程 process: 运行的代码 = 进程(不开多进程的情况) 
    - 查看进程: `ps aux | grep xxx`
    - 进程包含的资源
      - 环境变量 `env`: **进程皆有环境**
        - `PATH`
  - 线程 thread: 进程的执行单元, 交给操作系统管理
    - `pstree -p pid`
    - thread -> os 调度 -> cpu
  - 协程: 用户态的线程, 用户自己管理, 之后交给操作系统
    - 程序调度 vs os 调度
    - CPU密集型 vs io密集型

# 思维方式

- 分层
- 生命周期 = 执行顺序
- 思维导图
- 画图/实操 来理解概念性的内容

# 职业发展

- 技术 - 和机器交流: 编程基础 -> 胜任业务 -> 技术 blog -> 阅读源码 -> 开源 -> 架构设计
- 业务 - 和团队交流: 了解业务 -> 领域/行业 -> owner/团队