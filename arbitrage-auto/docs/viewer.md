# 可视化分析模块 

## 二元价差记录
说明
- 需要jqdata数据注入 
- 定时任务，每周6执行一次，

```
# 快速启动
bash scripts/script_viewer_arbi.sh
```

## 三元价差监控
说明
- 需要jqdata数据注入 
- 定时任务，每天执行一次，

```
# 快速启动
bash scripts/script_viewer_ftf.sh
```

## tick数据可视化
说明
- 需要进入代码，配置需要查看的品种&期限
- 需要联合 tick-baiduyun-data使用
```
python viewer/tick_margin_viewer.py
```
