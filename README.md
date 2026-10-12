# hongguo-mac-backup

红果短剧 macOS 客户端 **1.2.1** 的离线备份。

上游原始地址如果哪天挂了（这类仓库被 DMCA 或被作者删除是常事），这里的副本还能用。

- 备份日期：2026-10-12
- 来源：https://github.com/jackotom/hongguo-drama/releases/tag/v1.2.1
- 许可证：GPL-3.0（上游原始许可证，本仓库按同样条款再分发）

---

## 一、我要下载哪个文件？

| 你的机器 | 下载 |
|---|---|
| M 系列芯片 Mac（M1/M2/M3/M4…） | `Hongguo-1.2.1-mac-arm64.dmg` |
| Intel 芯片 Mac | `Hongguo-1.2.1-mac-x64.dmg` |

**文件在本仓库的 Releases 页面**（不是文件列表里，因为安装包 158 MB，超过 GitHub 单文件 100 MB 的 git 限制，只能作为 Release 附件分发）：

👉 https://github.com/z6284181/hongguo-mac-backup/releases

不确定自己是什么芯片：`uname -m` → 输出 `arm64` 选 arm64 版，输出 `x86_64` 选 x64 版。

---

## 二、安装

1. 双击 `.dmg`
2. 把「红果短剧.app」拖进「应用程序」
3. 从启动台或应用程序文件夹打开

上游 1.2.1 的 Mac 包已通过 Apple **Developer ID 签名 + 公证（notarization ticket 已装订）**，正常双击即可打开，不需要 `右键 → 打开`，也不需要关 SIP。

首次打开进「设置」→ 选好下载目录 → 保存。之后就正常用了。

---

## 三、校验下载的文件没被改过

下载完先跑一次，确认哈希与官方一致：

```bash
shasum -a 256 Hongguo-1.2.1-mac-arm64.dmg
```

应该得到：

```
846c8baea88d1450300c6203f4b95acb66e9d72c189ff5011dedc52960ed1541
```

（x64 版：`fe1909e93b80779fb0cc5fd6480d2c3b7b22acd7546fb6f75244dac136fd7b01`）

完整清单见仓库根目录 [`SHA256SUMS.txt`](./SHA256SUMS.txt)，与上游附件逐字节一致。

装好后还可以验证签名：

```bash
codesign -dv --verbose=2 "/Applications/红果短剧.app"
# 期望：Authority=Developer ID Application: JINHAO LI (P68PJVP59P)
#       Notarization Ticket=stapled

spctl -a -vvv -t exec "/Applications/红果短剧.app"
# 期望：accepted / source=Notarized Developer ID
```

---

## 四、仓库里还有什么

| 文件 | 说明 |
|---|---|
| `Hongguo-1.2.1-mac-arm64.dmg` / `mac-x64.dmg` | 安装包，在 **Releases** 里 |
| `hongguo-drama-1.2.1-source.zip` | 上游完整源码（GPL-3.0 要求随二进制一并提供） |
| `SHA256SUMS.txt` | 上游官方哈希清单，用于校验 |
| `红果短剧Mac版调研与安装.md` | 2026-10-12 的调研记录：GitHub 上有哪几个 Mac 版、各自可信度、安装与安全审计过程 |
| `UPSTREAM.md` | 上游信息与再分发声明 |

---

## 五、注意事项

- 这是**第三方非官方客户端**，与红果短剧官方无关，也不代表官方授权。
- 依赖上游接口，随时可能失效；上游若更新，本备份不会自动跟进。
- 内容版权归红果短剧及各版权方所有。**仅供个人学习与自用，禁止商用、禁止传播内容。**
- 使用本备份产生的任何后果自负。
