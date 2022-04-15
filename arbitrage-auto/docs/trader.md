# 交易模块 

## 参数配置

环境配置
```
# 配置策略具体规则
configs/strategy_config/*.json

# 配置实盘账户信息
configs/user_info_live.json

# 配置模拟盘账户信息
configs/user_info_simnow.json
```

## 启动脚本

快速启动
```
bash scripts/script_trade_zcl.sh

bash scripts/script_simnow_zy.sh
```

手动启动
```
python trader.py \
    --user hongyuan_zcl \
    --passwd xxx \
    --strategy_config 1_1_arbi_zy_live \
    --jq_auth zcl \
    --load_length 25 \
    --init_new_config \
    --run_child  \
    --force_load_data \
```