# img-installer
它是一個基於 Debian Live 系統的 img 映像安裝器。採用 GitHub Actions 構建打包。目前已實現在 x86-64 裝置上快速安裝 Armbian 和 OpenWrt 的功能。 
![1](https://github.com/user-attachments/assets/6635cb83-6164-4be7-ab1e-fff421b3dc2f)

## 背景解讀
- 嵌入式裝置的系統通常採用 img 格式，常見於 ARM 裝置，安裝方式通常是線刷、燒錄 SD 卡等。
- 但近年來，OpenWrt 和 Armbian 也逐漸相容並適配通用型 x86-64 裝置，隨著軟路由和 NAS 虛擬機的普及。
- 顯然針對 ARM 裝置的燒錄方法不太適合 x86-64 裝置（含虛擬機）。無論是借助 PE 還是使用 dd，都需要傳遞韌體檔案，顯得低效率且複雜。
- 如何讓 OpenWrt/Armbian 等小眾 x86-64 的 Linux 系統像安裝普通系統一樣簡單呢？希望本專案能給你一個滿意的答案。

## 使用方式
[圖文教學](https://club.fnnas.com/forum.php?mod=viewthread&tid=26293)
1. 虛擬機使用：各種虛擬機直接選擇 ISO 即可
2. 實體機使用：建議將 ISO 放入 Ventoy ��隨身碟中
3. https://www.ventoy.net/cn/download.html
4. 視頻教學：[![YouTube](https://img.shields.io/badge/YouTube-123456?logo=youtube&labelColor=ff0000)](https://youtu.be/6FWyACrNQIg)
[![Bilibili](https://img.shields.io/badge/Bilibili-123456?logo=bilibili&logoColor=fff&labelColor=fb7299)](https://www.bilibili.com/video/BV1DQXVYFENr)
- 【第一集 ESXI 虛擬機 和 實體機使用】https://youtu.be/6FWyACrNQIg   【B站】https://www.bilibili.com/video/BV1DQXVYFENr
- 【第二集 飛牛 NAS】https://youtu.be/RRBFc58SwXQ  【B站】https://www.bilibili.com/video/BV1gPXCYyEc2
- 【第三集 Hyper-V、綠聯 NAS 虛擬機、飛牛虛擬機使用教學】 https://www.bilibili.com/video/BV1BoZVYsE7b
- 【第四集 PVE 虛擬機裡如何使用 img 安裝器】https://www.bilibili.com/video/BV1Rx5Qz4EZB

6. 具體的操作方法是：在安裝器所在的系統裡輸入 `ddd` 命令，即可喚出安裝選單
   ![localhost lan - VMware ESXi 2025-03-20 10-14-45](https://github.com/user-attachments/assets/ddae80a0-9ff5-4d63-83b5-1f49da18b008)


## 項目說明與相關功能
1. 本專案生成的 ISO 同時支援實體機與虛擬機的安裝
2. 本專案生成的安裝器用於各種常見的 img 格式嵌入式系統：`OpenWrt`、`Armbian`、`HAOS`、`LibreELEC` 等
3. 其中 OpenWrt 分為 istoreos、immortalwrt、EzOpWrt、eSirOpenWrt 安裝器。實際上安裝任意一種即可，因為可在網頁中隨時更換韌體。
4. istoreos 在虛擬機上並沒有安裝器，因此本專案算是一種補充。（實體機安裝 istoreos 時可忽略本專案）
5. Armbian 安裝器目前構建兩種：一種是 minimal，一種是標準版。較低配置的 x86-64 裝置建議使用 minimal，例如（Wyse3040 瘦客戶機）
6. HAOS 可自訂下載地址，預設構建 HAOS 15.0 `haos_generic-x86-64-15.0.img.xz`
7. 支援自訂 OpenWrt 映像生成 ISO 安裝器，其中 OpenWrt 映像的壓縮包格式為 `img.gz`、`img.zip`、`img.xz` 三種


## ISO 自動製作流程
本專案亦基於開源專案 [debian-live](https://github.com/dpowers86/debian-live) 製作，因此我的程式碼全程開源，MIT 協議不變。
1. 首先構建一個 Debian Live 系統，該系統帶有 EFI 引導。
2. 在該系統內融入我們需要的 img 映像與自行製作的 dd 寫盤腳本，一起打包到 filesystem.squashfs 檔案系統中。該過程包含壓縮，從而保證最終體積較小。
3. 最後將新的 squashfs 檔案與相關檔案一起打包為 ISO

## 項目參考
- https://willhaley.com/blog/custom-debian-live-environment/
- https://github.com/dpowers86/debian-live
- https://github.com/sirpdboy/openwrt/releases
- https://github.com/esirplayground

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=wukongdaily/armbian-installer&type=Date)](https://star-history.com/#wukongdaily/armbian-installer&Date)


## ❤️ 贊助作者 ⬇️⬇️
#### 專案開發不易，感謝您的支持與鼓勵。<br>
[![點擊這裡贊助我](https://img.shields.io/badge/点击这里赞助我-支持作者的项目-orange?logo=github)](https://wkdaily.cpolar.cn/01) <br>