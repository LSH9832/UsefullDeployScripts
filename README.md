# UsefullDeployScripts：有用的部署脚本

## 前言
linux（debain系）一些有用的部署脚本，整理在此

如果大家有什么新的需求，请在issue里提出

使用前请赋权
```shell
chmod +x scripts/*
```
## 列表
| 名称 | 用途 | 类型 | 链接 |
|:----|:-----:|:---:|:---:|
|add_startup_service|添加开机自启服务|python3|[文档](/docs/add_startup_service.md)<br>[源码](/scripts/add_startup_service)|
|back_run|后台运行指定命令|bash|[文档](/docs/back_run.md)<br>[源码](/scripts/back_run)|
|launch|多程序启动+看门狗|python3|[文档](/docs/launch.md)<br>[源码](/scripts/launch)|
|ping_until_success|执行ping直到ping通|bash|[文档](/docs/ping_until_success.md)<br>[源码](/scripts/ping_until_success)|
