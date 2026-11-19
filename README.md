### Hi there 👋

我是 **Aaron-XSJ**，在合肥，做嵌入式和硬件 DIY：从 STM32 固件、SDIO / SPI 驱动，到 BLE 设备和微信小程序，喜欢把一块开发板做成能摆在手边、能摸得到的实物。

🛠️ 常用：`STM32F103` · `Keil MDK` · `C` · `FatFs` · `SPI / SDIO` · `VS1003` · `BLE` · `Git`

---

## 🔖 正在做：EPD —— 会播放音乐的 CD 冰箱贴

一枚贴在冰箱上的音乐冰箱贴：**电子墨水屏常驻显示 CD 封面**，配上曲名与进度，按键切歌，小喇叭出声。尺寸按怀旧 CD 盒来做；不播的时候封面也留在屏上，像一张摆在冰箱门上的唱片封套。

<p align="center">
  <img src="./assets/epd-cd-fridge-magnet.svg" width="680" alt="EPD：CD 封面冰箱贴产品形态示意">
</p>

> 选墨水屏，是因为断电保图、静态几乎不耗电、类纸质感接近印刷封面；只在切歌时刷新一次，反而更像实体唱片，而不是一块常亮的小电视。

**当前进度**：播放链路已经跑通。STM32F103ZE 经 SDIO 4-bit 读 TF 卡，FatFs 取文件，SPI1 喂给 VS1003 硬件解码；核心是 **双缓冲（乒乓）+ DREQ 流控** —— 把读卡耗时藏在解码时间里，缓冲切换只换指针不拷贝，裸机、无 DMA 参与也能连续出声、**不卡顿**。

👉 [查看 EPD 仓库](https://github.com/Aaron-XSJ/EPD) · [双缓冲为什么不卡顿](https://github.com/Aaron-XSJ/EPD#双缓冲喂数据播放为什么不卡顿)

| 模块 | 状态 | 说明 |
| --- | --- | --- |
| 音频播放 | ✅ 已跑通 | SDIO + FatFs + VS1003，双缓冲连续播放、切歌 / 暂停、每曲独立复位 |
| 电子墨水屏 | ⏳ 规划中 | 建议走独立 SPI2，避免全刷打断喂数据 |
| CD 封面 / 元数据 | ⏳ 规划中 | 封面在 PC 端预转 1bpp 位图，按曲名索引送屏 |
| 电池 / 功放 / 外壳 | ⏳ 规划中 | CD 盒比例、背面磁贴、小喇叭、可换 TF 卡 |

---

## 📦 开源项目

| 项目 | 一句话 | Stars |
| --- | --- | --- |
| [EPD](https://github.com/Aaron-XSJ/EPD) | STM32F103 + VS1003 双缓冲 MP3 播放器，目标是电子墨水屏 CD 封面冰箱贴 | [![Stars](https://img.shields.io/github/stars/Aaron-XSJ/EPD?style=flat&label=Stars)](https://github.com/Aaron-XSJ/EPD/stargazers) |

---

## 🧰 工具与方向

- 硬件：STM32F103 核心板、TF 卡（SDIO）、VS1003 解码模块
- 软件：Keil MDK / C / FatFs R0.11 / Git
- 也在折腾：BLE 固件、微信小程序、HarmonyOS / Android 小工具

📫 想聊硬件或项目，欢迎到 [EPD 仓库提 issue](https://github.com/Aaron-XSJ/EPD/issues)。

[查看全部仓库 →](https://github.com/Aaron-XSJ?tab=repositories)
