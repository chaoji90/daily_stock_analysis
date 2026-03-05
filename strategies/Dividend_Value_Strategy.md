name: dividend_value
display_name: 红利价值策略
description: 筛选具有高股息率、稳定现金流且估值合理的防御型股票。适用于震荡市或长线价值配置。
category: value
core_rules: [1, 5]
required_tools:

get_financial_reports

get_dividend_history

get_valuation_metrics

instructions: |
红利价值策略（Dividend Value Strategy）

评估标准：

股息率（Dividend Yield）筛选：

使用 get_valuation_metrics 检查当前静态与滚动股息率。

核心标准：股息率 > 4% 或高于行业平均水平 1.5 倍。

分红稳定性与历史（关联理念1：严进策略）：

使用 get_dividend_history 查看过去 3-5 年的分红记录。

要求：分红从未间断，且分红金额保持平稳或逐年增长（Dividend Aristocrats 逻辑）。

财务安全性（分红支付能力）：

使用 get_financial_reports 检查 Payout Ratio（股息发放率）。

理想区间：40% - 70%。过高（>90%）可能导致分红不可持续，过低则缺乏诚意。

检查 自由现金流（FCF） 是否为正，确保分红是由真金白银支撑，而非举债分红。

估值水位线：

对比历史市盈率（PE）与市净率（PB）分位点。

触发条件：当前股息率处于近五年高位（即股价处于相对底部区间）。

动能与防御性检查（关联理念5：安全边际）：

检查贝塔系数（Beta）。理想状态下 Beta < 0.8，说明该股在市场下跌时具有较强的抗跌性。

评分调整：

股息率 > 5% 且现金流覆盖充足：sentiment_score +12

连续 5 年增加分红（Dividend Growth）：额外 +8

若 Payout Ratio 持续恶化或净利润连续下滑：直接扣除 15 分并在 risk_warning 中注明。

在 buy_reason 中注明“红利价值策略：高股息支撑与财务稳健”。
