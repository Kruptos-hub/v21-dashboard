# KrupStockSys V21 实时信号仪表盘

iPad / Safari 友好的 A 股量化信号看板，行情通过腾讯财经接口实时推送（无需自建服务器）。

© 2026 Kruptos · 保留所有权利

## 永久地址
https://kruptos-hub.github.io/v21-dashboard/

## 访问控制（私有看板）
看板数据使用 **AES-256-GCM** 加密后内嵌页面，打开后需输入访问密码才能解密查看。
GitHub Pages 本质是公开托管，但内容已加密，未授权者即使拿到链接也看不到信号。
- 密码在生成时由部署方设定，存于本地 `data/inference/.dashboard_pass`（不入库）。
- iPad 上首次输入密码后会缓存在本机，之后免输。
- 通过 HTTPS 打开才能解密（本地 `file://` 不支持 Web Crypto，请用本仓库的 `.webarchive` 离线版）。

## 特性
- 纯静态单文件，iPad Safari 直接打开
- 访问密码锁（数据加密，防止他人窥探持仓）
- 底部 Tab 切换（主仓 / 波段 / 回避 / 全部）
- 显示股票**名称** + 代码 + 模型评分
- 每 30 秒通过 `qt.gtimg.cn` 拉取实时价格与涨跌幅（CORS 开放，无需代理）
- 信号由云端 V21 模型训练后生成，iPad 只接收轻量信号流

## 更新方式
云端设置环境变量后重跑流水线，信号会自动加密并推送：
```bash
DASHBOARD_PASS=你的密码 bash scripts/run_v21_live.sh   # 会自动导出加密版并部署
```
也可手动：将新生成的 `krupstocksys/data/inference/v21_dashboard_latest.html`
复制为 `index.html` 推送到本仓库 main 分支，GitHub Pages 自动生效。

> 想彻底不公开仓库：可将本仓库设为私有并升级 GitHub Pro 以使用私有 Pages；
> 或删除本仓库、改用本地 `.webarchive`（从 文件App 直接用 Safari 打开）。
