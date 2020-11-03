 # Define 
    1. WOE describes the relationship between a predictive variable and a binary target variable.
    2. IV measures the strength of that relationship.
# Step
    1 连续型变量进行分箱 binning
        等频
        等距
        自定义间隔
      离散型变量 若是分箱太多要进行合并
    
    2 计算每个箱子中好和坏样本的数量

    3 分别计算每个分箱中 好、坏样本占总体好、坏样本的比例
        repeat for every bin
        margin_good_rate = good_num_in_this _bin / total_goods
        margin_bad_rate = bad_num_in_this _bin / total_bads

    4 计算 WOE
        WOE = ln （margin_bad_rate / margin_good_rate )
    
    5 检查单调性
        不单调则返回步骤1 重新分箱
    
    6 计算 IV 
# 单调性
# 个人理解 
    WOE_i = ln （ margin_bad_rate / margin_good_rate )

        = ln (( bad_i / bad_total )  / (good_i / good_total ))

        = ln ( bad_i / bad_total )  - ln (good_i / good_total )
    本质是在计算第i箱内的数据分布偏离总体均值的程度 

    IV_i  =  (( bad_i / bad_total )  -  (good_i / good_total )) * WOE_i

    本质也是在计算第i箱内的数据分布偏离总体均值的程度 

    