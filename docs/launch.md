# launch：适用于单个/多个程序的同时启动脚本

launch是一个基于python3的脚本，需要安装的第三方库有：
- `pyyaml`

如果不方便安装第三方库，请将下述配置文件改为json格式进行编写并在脚本中相应的读取并解析yaml文件的接口的位置改为读取并解析json文件的接口
launch通过读取yaml配置文件对对应的程序进行运行管理，具体用法为：
```bash
launch_path="/path/to/this/script/launch"
$launch_path /path/to/your/yaml/file.yaml -t 0.5  # 每0.5秒检查一次程序是否还在运行且是否需要重启，默认0.1秒
```
其中yaml的配置文件格式如下所示
```yaml
one_exec_node:   # 第一个程序名称，可随意命名，不要与文件中其他程序名称重合即可
  # 在何路径下运行该程序，没有该字段则默认在当前路径下运行
  work_dir: /run/dir
  # 运行程序的命令，该字段是唯一必须存在的字段，支持在运行对应命令之前添加其他语句，如本行所示
  command: export LD_LIBRARY_PATH=$LD_LIBRARY_PAYH:/run/dir/lib;./test1
  # 是否只运行一次，如果是，则不会在程序退出后重新运行，删除此字段默认会重启
  run_once: false
  # 用于定位程序pid从而在必要时通过kill命令结束该程序，建议从optArgs里选择，没有此字段有可能无法终止该程序
  kill_keyword: ["./test1", "/path/to/your/config.ini"]
  # 是否将程序中的log写入文件，仅当程序的optArgs中有--add-log且程序中的logger支持时生效，此时无需在下方optArgs填写而转移到此处填写，否则必须填false或删除此字段
  write_log: true
  # 写入log的文件夹路径，仅当程序的optArgs中有--add-log时生效，否则请删除此字段
  log_path: /dir/of/your/log/file
  # log文件名称，仅当程序的optArgs中有--add-log时生效，否则请删除此字段
  log_file: .log
  # log文件是否加上时间戳，用以分开每一次运行时的log文件，仅当程序的optArgs中有--add-log时生效，否则请删除此行
  log_filename_addtime: true
  # 位置参数, list， 没有则填null或删除此字段
  posArgs: ["/dev/video0"]
  # 可选参数，dict，参数名和参数值由空格隔开，若程序要求用等号隔开请直接写在command中。其中内容根据实际程序设置填写, 没有则删除此字段
  optArgs:
    --config-file: /path/to/your/config.ini
    --debug: false
    # --add-log: "/path/to/log/file.log"   # 仅示意，移到上方填写
```
