## 红果短剧 macOS 客户端 1.2.1 · 离线备份

上游：https://github.com/jackotom/hongguo-drama/releases/tag/v1.2.1

### 下载

| 机型 | 文件 |
|---|---|
| M 系列芯片 Mac（M1/M2/M3/M4…） | `Hongguo-1.2.1-mac-arm64.dmg` |
| Intel 芯片 Mac | `Hongguo-1.2.1-mac-x64.dmg` |

不确定机型：终端跑 `uname -m`，输出 `arm64` 下 arm64 版，输出 `x86_64` 下 x64 版。

### 安装

1. 双击 DMG
2. 把「红果短剧.app」拖进「应用程序」
3. 直接打开（该包已通过 Apple Developer ID 签名 + 公证，无需右键打开、无需关 SIP）

### 校验（建议做一次）

```bash
shasum -a 256 Hongguo-1.2.1-mac-arm64.dmg
```

应当输出：

```
846c8baea88d1450300c6203f4b95acb66e9d72c189ff5011dedc52960ed1541
```

x64 版对应哈希：`fe1909e93b80779fb0cc5fd6480d2c3b7b22acd7546fb6f75244dac136fd7b01`

完整清单见仓库根目录 `SHA256SUMS.txt`。二进制与官方原件逐字节一致，未做任何改动。

### 许可证与来源

- 上游以 **GPL-3.0** 授权，本备份按同样条款再分发
- 对应源码已随仓库提供：`hongguo-drama-1.2.1-source.zip`
- 上游签名主体：`Developer ID Application: JINHAO LI (P68PJVP59P)`
- 本备份非上游官方渠道，不作任何担保

详见仓库内 `UPSTREAM.md` 与 `README.md`。
