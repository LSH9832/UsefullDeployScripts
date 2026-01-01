# back_run：后台启动程序脚本

back_run是一个基于bash的脚本，可以实现程序快速在后台启动，需要的依赖有
- `screen`，可通过`sudo apt install screen`安装，若未安装，该脚本第一次运行时会自动尝试安装

其用法为：
```shell
# 脚本路径 后台窗口命名（请勿与其他后台窗口重复） 启动程序命令
./back_run <screen_name> <command...>

# 示例
./back_run launch_test ./launch /path/to/config.yaml -t 0.5 # 从第二个参数开始都是启动程序命令
```
