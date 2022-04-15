# 交易&记录报警模块

## 使用方式

- 基本参数设定，参考 
```
configs/email.json
```

- 基本启动脚本
```
# 启动交易报警
scripts/script_alert.sh 

# 启动记录报警
scripts/script_alert_recorder.sh

# 手动启动记录，fifo-path需要对应中间logging文件
python alerter.py \
    --fifo_path terminal.fifo \
    --err_alert \
    --start_alert
```

## 报警方式

- 邮件报警，使用网易邮箱，订阅如下账号密码 
    -  xxx@126.com

## 报警场景

- 成交通知
    - 实盘
    - 模拟盘

- 异常报警
    - 实盘
    - 模拟盘
    - 记录模块
    - 数据模块

