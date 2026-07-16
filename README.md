# KrupStockSys V21 实时信号仪表盘

iPad / Safari 友好的 A 股量化信号看板，行情通过腾讯财经接口实时推送（无需自建服务器）。

## 永久地址
https://kruptos-hub.github.io/v21-dashboard/

## 特性
- 纯静态单文件，iPad Safari 直接打开
- 底部 Tab 切换（主仓 / 波段 / 回避 / 全部）
- 显示股票**名称** + 代码 + 模型评分
- 每 30 秒通过 `qt.gtimg.cn` 拉取实时价格与涨跌幅（CORS 开放，无需代理）
- 信号由云端 V21 模型训练后生成，iPad 只接收轻量信号流

## 更新方式
云端重跑 `run_v21_live.sh` 后，将新生成的
`krupstocksys/data/inference/v21_dashboard_latest.html`
复制为 `index.html` 并推送到本仓库 main 分支即可。
GitHub Pages 会自动生效。
