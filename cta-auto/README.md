Update time: 2020-8-29:13:45
0. 安装配置
    a. ubuntu 16 更新 gcc 7.0， 可以寻找 ppa 源快速安装, ubuntu 18 无需更新
        sudo add-apt-repository ppa:ubuntu-toolchain-r/test
        sudo apt-get update
        sudo apt-get install -y g++-7
        cd /usr/bin 
        sudo rm -rf gcc 
        sudo ln -s gcc-7 gcc 
        sudo rm -rf g++ 
        sudo ln -s g++-7 g++
    b. 彻底放弃适配Windows
    c. vnpy-auto 应该放在根目录， vnpy-auto 中建立 .vntrader 文件夹
    d. 配置vt_setting.json, 设置使用 mongodb 数据库, 并且安装 apt-get install mongodb

1. 源码修改 
    a. 为防止冲突，删除vnpy/app/cta_stragegy/strategies 以防止冲突 (TODO: 该自己的策略名字)
    c. vnpy_modified 替换 python 路径下的vnpy文件
    d. 自动化修改 python install_local.py 
    
2. 回测脚本 
    a. python auto_optim.py --func [init, resume] --target_fn sharpe_drawback_fn --xmin 10
    b. --date_stamp 8_1 表明回测的最后一个阶段的时间
    c. 优化过程中的目标函数在 auto_optim/target_fns.py 中修改，./auto_optim.py 中注册 目前包含[sharpe_fn， sharpe_linear_fn， sharpe_drawback_fn]
    d. 根据主机名称自动分配待优化的策略，在 strategy_group 中定义
    e. condidate.json, analysis.csv 中粗略筛选策略

3. 实盘脚本 trader.py, 正在实测中 
    a. 每日8：45， 20：45 自动调用 jqdata_load 更新数据, 不可以在21；00之后再启动！！，无法导入jqdata数据
    b. python trader.py --user xxx --passwd xxx [--run_child] [--init_new_config]
    c. 如果更新策略，先手动平层，然后加入 --init_new_config, 会删除 cta_stragegy_data, cta_stragegy_settting
    b. auto_trade/panel.txt 实时检测仓位，订单信息, auto_optim/strategy_status.txt 实时检测策略状态
    c. auto_trade/log 查看运行LOG 
    d. .vntrader/ 查看缓存信息 cta_stragegy_data, cta_stragegy_settting
    e. 务必将实盘Symbol加入 LivePool，否则不会成功导入数据
    
4. 数据导入命令
    python jqdata_load.py --func [init_new_machine, check_main_data, check_online_data, load_online, load_restore]
    
    新机器应手动导入 mongodb： 
    python jqdata_load.py --func init_new_machine
    python jqdata_load.py --func check_main_data
    python jqdata_load.py --func check_online_data
    python jqdata_load.py --func load_online --data_range 30

7. 每月检查一下换期
    a. 应该注意修改 basic_constant.py  中的 MonthChanges，
    b. 导入策略池中连续30天数据 python jqdata_load.py --func load_online --data_range 30
    c. 修改 auto_trade/strategy_*.json 中品种名称

