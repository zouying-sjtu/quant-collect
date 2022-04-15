# 记录模块 

## Tick记录
注意：
- 需要使用实盘账户构建一个TCP链接
- 交易所规定：单个账号连接数不得超过3次，例如APP连接一次，实盘连接一次，记录模块连接一次，一共三次

修改需要记录的配置
```
config/record_config/*.json
```

使用方式
```
# 自动使用
python scripts/script_record.zcl.sh

# 直接使用，term_recorder.fifo用于传递消息给报警模块
python recorder.py \
    --user hongyuan_zcl \
    --passwd xxx \
    --strategy_config 12_25_record >> term_recorder.fifo 2>&1;
```