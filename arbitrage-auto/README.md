# 量化自动化分析+交易

## 环境设置
### python安装配置
```
# 务必使用正确，否则API有差异
python=3.8
vnpy-2.1.8 

# 常规包
tzlocal 
mongoengine 
plotly 
jqdatasdk
easydict

# 清华源镜像
-i https://pypi.tuna.tsinghua.edu.cn/simple/
```

### 画图模块配置
```
conda install -c plotly plotly-orca
pip install psutil requests
sudo apt-get install xvfb
```

### github配置
```
ssh-keygen -t rsa -b 4096 -C "xxx@qq.com"
cat ~/.ssh/id_rsa.pub
paste to "https://github.com/settings/keys"
```

## 接口
### CTA simnow 
```
第一套
    180.168.146.187:10130
    180.168.146.187:10131
第二套
    180.168.146.187:10101
    180.168.146.187:10111
```

### CTA 宏远期货
```
第一套
    180.169.112.52:42205
    180.169.112.52:42213
```


## 功能：
如下功能皆可7x24h无需干预

- 交易模块 [trader.md](docs/trader.md)
    - 实盘交易 
    - 模拟盘交易

- 回测模块 [backtest.md](docs/backtest.md)
    - bar级回测 
    - tick级回测
    - 切片优化 & 智能分析

- 可视化分析模块 [viewer.md](docs/viewer.md)
    - 回归性分析 & 可视化
    - 定时任务记录 & 盘面异常分析

- 交易&记录报警模块 [alert.md](docs/alert.md)
    - 启动提醒 & 成交提醒
    - 异常报警 & 邮件通知

- 数据管理模块 [datamanage.md](docs/datamanage.md)
    - 数据库管理
    - 原始文件直读

- 算法分析模块 [analysis.md](docs/analysis.md)
    - 切片分析
    - 评估法
    - 机器学习法

- 记录模块 [recorder.md](docs/recorder.md)
    - tick 数据记录
    - 全行情记录（暂未使用）[fullrecorder.md](docs/fullrecorder.md)



