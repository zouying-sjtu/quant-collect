# 回测模块 

## Tick级

### 使用方式

- 基本参数设定，参考 
```
# 单批参数回测
configs/backtest_config/*.json

# 优化参数回测
configs/backtest_optim_config/*.json
```

- 基本启动脚本
```
# 单批参数回测
scripts/script_backtest_batch.sh 

# 优化参数回测
scripts/script_backtest_optim.sh 

# 手动回测, --pkg 代表是否单次使用循环数据
python backtest/backtesting_tick.py \
    --cfg_name "$cfg" \
    --pkg
```

- 辅助脚本
```
# 自动生成多个品种回测配置文件 （初步定品种）
python backtest/gen_cfgs.py --init
```


## Bar级

暂时停用

### 相关脚本
```
backtest/backtesting_optim.py

backtest/backtesting.py
```