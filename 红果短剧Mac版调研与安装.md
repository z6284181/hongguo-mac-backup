# 红果短剧 Mac 版 · 调研与安装记录

日期：2026-10-12
结论：**Mac 版早就有，不用自己做。** 已装好官方签名公证的开源版。

---

## 一、GitHub 上已有的 Mac 客户端（按可信度排序）

| # | 仓库 | 源码 | 签名/公证 | 平台 | 可信度 |
|---|---|---|---|---|---|
| 1 | `jackotom/hongguo-drama` v1.2.1 | ✅ GPL-3.0 全源码 | ✅ Developer ID + Apple 公证 | Mac arm64 / x64 + Win x64 | ★★★★★ 已安装 |
| 2 | `StriveToLearnCode/hongguo-short-drama-macos` v0.2.2 | ❌ 只发 DMG | 未验证 | Mac universal | ★★☆☆☆ 闭源二进制 |
| 3 | `xu-jin-cs/hongguo-desktop-mac` v1.2.0 | ✅ Electron+React+TS | 未验证 | 仅 Mac arm64 | ★★★☆☆ 需自行装 ffmpeg |
| 4 | `waligoraamodio288-rgb/hongguo-desktop-releases` | ❌ 只有 release | 未验证 | Win + Android TV | ⚠️ 近 3000 star 但无源码，典型可疑分发号 |
| 5 | `yangbin1322/hongguo-player` | ❌ | 未验证 | 引导到第三方域名 `hongguo.235698.xyz` | ⚠️ 不推荐 |

> 网上搜到的 `hongguoshiju.com` / `hongguo.juhaov.com` / `oppozhijia.com` 之类"PC 版入口"全是 SEO 垃圾站，不是官方，别点。

## 二、本次安装的版本

- 应用名：**红果短剧.app**
- 安装位置：`/Applications/红果短剧.app`（334 MB，arm64）
- 版本：1.2.1（2026-10-11 发布）
- 开发者签名：`Developer ID Application: JINHAO LI (P68PJVP59P)`
- 公证状态：`Notarization Ticket=stapled`，`spctl → accepted / Notarized Developer ID`
- 安装包 SHA-256：`846c8baea88d1450300c6203f4b95acb66e9d72c189ff5011dedc52960ed1541` ✅ 与官方 `SHA256SUMS.txt` 一致

### 已做的安全检查

1. 下载源码包，比对官方哈希 → 一致。
2. 静态审计源码：
   - `src/native/hongguo.js` / `xifan.js` / `hema.js` = 三个内容来源
   - 域名只出现 `hongguoduanju.com`、`youlishipin.com`、`kuaikaw.cn`、`fqnovel.com`、`byteimg.com`（封面图）
   - 无 `child_process` 调用（应用层）；无 `eval` / webhook / 埋点上报
   - 更新源只指向本仓库 GitHub Releases
   - 测试用例里有 `evil.test` / `attacker.test` 域名，是 SSRF 防护测试，属正面信号
3. 安装包 `codesign` + `spctl` 双验证通过，并已启动成功（PID 已确认）。

## 三、使用要点

- 首次打开进「设置」→ 选下载目录 → 保存。
- 「发现短剧」浏览 / 「搜索与下载」搜剧名；红果、西饭、河马三来源并搜。
- 支持横屏 / 竖屏、窗口置顶、0.25×–4× 倍速、断点续播、缓存下一集。
- 内置 ffmpeg，无需 `brew install`。

## 四、注意事项

- 非官方客户端，不受红果官方支持，接口随时可能失效。
- 「下载 + 合并导出」功能涉及内容版权，**自己看可以，别转发传播**。
- 安装包留在 `~/Downloads/hongguo-mac/`（158 MB），确认没问题后可删。
