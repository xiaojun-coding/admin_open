## 项目概述

技术栈基于 `vite + vue3( options api ) + element-plus + pinia + axios`

代码切分基于**模块化**的方式组织代码架构

对于小项目可以快速开发，对于大型项目，以及多人协作，无论是代码的综合管理性，可维护性，可扩展性都可以很好的满足


## 开发

```bash
# 克隆项目
git clone https://gitee.com/opendeer/xiaoluxian_vue.git

# 安装依赖，建议使用 pnpm
pnpm install

# 启动服务
pnpm dev

# 打包
pnpm build
```

## 功能

- 登录 / 注销
- 权限验证
    - 页面权限（可精细化到，路由和菜单的重定向）
    - 字符权限（根据配置细化到任意节点）
    - 权限配置
    - 字典配置
- 动态面包屑
- 静态路由动态配置化，支持嵌套
- Screenfull 全屏
- 环境配置（任意环境）
- axios 全量封装（get, post, 静态文件类，流文件），权限，loading，请求延迟，等
- 代码格式化（自动格式化 + prettier配置）
- vite 配置（代理模板 + 常用插件继承）

## 目录结构

```
├── .vscode                        # 自动格式化
├── modules                        # 核心的源码模块
│   └── common                     # 全局`业务`公共组件
├── public                         # 静态资源
│   └── favicon.ico                # ico 图标
├── src                            # 全局文件和启动文件
│   ├── api                        # 放置全局范围 API
│   ├── assets                     # 静态资源
│   │   ├── css                    # 全局CSS
│   │   │   ├── custom.init.css    # 自定义的全局CSS
│   │   │   └── init.css           # 初始化样式CSS
│   │   └── images                 # 全局图片
│   ├── constants                  # 全局常量
│   │   ├── crypto.js              # 加密相关
│   │   ├── env.config.js          # 全局环境变量
│   │   ├── icons.js               # 全局图标的 KEY
│   │   └── regexp.js              # 全局的正则表达式
│   ├── router                     # 路由
│   │   ├── guards.js              # 路由守卫，权限校验
│   │   ├── index.js              
│   │   ├── route.js               # 定义路由的地方
│   │   └── router.js              
│   ├── share                     # 全局和状态无关的公共逻辑
│   │   ├── helper                 # 工具函数
│   │   ├── progress               # 全局进度条
│   │   └── request                # axios封装
│   │       └── basic              # 默认基础请求
│   │           ├── index.js 
│   │           ├── proxyRequest.js # 三次封装 
│   │           └── request.js     # 二次封装 
│   └── store                      # 全局的状态管理
│   │   ├── EnumGlobalStore.js     # 字典相关
│   │   ├── GlobalStore.js         # 全局统一入口
│   │   ├── MenuGlobalStore.js     # 权限菜单方面
│   │   └── UserGlobalStore.js     # 个人消息方面
│   ├── components                 # 全局`静态`公共组件
│   ├── App.vue                    # 根 vue 文件
│   ├── main.js                    # 程序入口
├── jsconfig.json                  # 配置路径识别
├── index.html                     # spa的模板 html
├── vite.config.js                 # vite 配置
├── package.json                   
└── readme.md
```