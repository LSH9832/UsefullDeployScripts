# add_startup_service：添加开机启动服务

[add_startup_service](/scripts/add_startup_service)是一个基于python3的脚本，可以方便地添加开机启动服务，需要在root权限账户下运行，其用法为

```bash
./add_startup_service --name service_name \ # 服务名称，用于生成.service文件
                      --command "python3 /path/to/main.py" \ # 服务启动时执行的命令
                      --comment "a python script" \          # 服务描述，可不填
                      --network \                            # 该服务需要网络服务支持
                      --no-start                             # 仅在当前目录下生成service文件，不添加到开机启动中
```
