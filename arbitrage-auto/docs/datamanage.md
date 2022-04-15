# 数据管理模块 

## 数据下载
- 实盘下载方式：

使用JDdata免费版本，但是可以使用100w条，账户配置如下
```
zy:
    account: xxx
    passwd:  xxx
```

- 使用方式
    - 依赖mongodb，下载后自动导入mongodb
    - 说明：使用">> terminal.fifo 2>&1;"记录数据下载log，并送报警模块查看（jqdata接口偶尔出异常）
```
python data_manage/jqdata_load.py \
    --strategy_config 11_1_arbi_zcl_live \
    --func load_live \
    --data_range 40 \
    --auth zcl  >> terminal.fifo 2>&1;
```


## 数据库管理
使用mongodb/sql，需要提前配置 ".vntrader/vt_setting.json"

```
# 每个月换月时从 JQdata 导入新一个月的<<回测数据>>：
python jqdata_load.py \
    --func load_restore \
    --auth zcl \
    --restore_month 2021-5-1 \
    --start_date 2021-3-1 \
    --end_date 2021-5-10

# 每个月换月时从 JQdata 导入新一个月的<<实盘数据>>：
python jqdata_load.py --func load_live --data_range 30 --auth zcl 

# 从csv直接导入 <<某个月的回测数据>>
python jqdata_load.py --func init_new_machine --restore_month 2020-10-1
    
# 从csv直接导入 <<所有回测数据>>
python jqdata_load.py --func init_new_machine --restore_month all

```


## 原始文件直读
直接读入csv文件中的数据，并构造TickDataDB，可直接用于回测

- 代码已经嵌入"modified/arbi/backtesing_engine_tick.py"，Tick级回测时自动导入
- 若想直接调用可以使用如下脚本
- 当前数据存在于 "xxx"

```
python data_manage/load_tick_manual.py
```