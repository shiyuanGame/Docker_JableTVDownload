# Docker_for_JableTVDownload

感谢 @Road-tech 大佬的贡献和耐心解答

[https://github.com/Road-tech/Docker_JableTVDownload](https://github.com/Road-tech/Docker_JableTVDownload) 我梭哈大佬的代码 修改了检查本地是否存在如果存在就不进行下载，还对影片文件进行影片标题的命名。

使用教程

`docker run -v /Your/download/dir:/data -e URL="`

------------------------------分割线---------------------------------

[JableTVDownload](https://github.com/hcjohn463/JableTVDownload) 是一款由[hcjohn463](https://github.com/hcjohn463)使用 python 开发的 JableTV 下载器。

本镜像能帮助用户减少运行环境的配置工作，可以更简单的使用。

本镜像目前仅支持 x86 环境。

因为原作者专注于 Windows 环境，软件更新后不一定能兼容 Linux 环境下。本人 fork 了[hcjohn463](https://github.com/hcjohn463)的仓库，会在测试没问题后再构建镜像。

故本镜像从仓库我 fork 的 [JableTVDownload](https://github.com/Road-tech/JableTVDownload) 构建，很可能不会及时和上游 release 同步，见谅。

使用教程

`docker run -v /Your/download/dir:/data  -e URL="https://jable.tv/videos/ssis-XXX/" road001/jabletv_dl`

或者

`docker run -v /Your/download/dir:/data  -e URL="https://jable.tv/videos/ssis-XXX/"  ghcr.io/road-tech/docker_jabletvdownload:main`

# JableTVDownload 介绍

## 下載 JableTV 好幫手

每次看正要爽的時候就給我卡住轉圈圈

直接下載到電腦看沒煩惱

### 1.搭建並啟用虛擬環境(Activate Virtual Environment)

```
python -m venv jable
jable/Scripts/activate
```

![image](https://github.com/hcjohn463/JableDownload/blob/main/img/createVenv.PNG)

### 2.下載所需套件、檔案(Download Requirement Files)

`pip install -r requirements.txt`

![image](https://github.com/hcjohn463/JableDownload/blob/main/img/requirements.PNG)

下載 ChromeDriver 至資料夾 [ChromeDriver][ChromeDriver]

![image](https://github.com/hcjohn463/JableDownload/blob/main/img/chromeDriver.PNG)

安裝 [FFmpeg][FFmpeg] (未安裝也能下載 但影片拖拉時間軸會有卡幀情況發生)

### 3.執行程式(Execute)

`python main.py`

### 4.輸入影片網址(Input Video Url)

`https://jable.tv/videos/ipx-486/`
![image](https://github.com/hcjohn463/JableDownload/blob/main/img/download2.PNG)

### 5.等待下載(Wait Download)

![image](https://github.com/hcjohn463/JableDownload/blob/main/img/finish.PNG)

### 6.完成(Finish)

![image](https://github.com/hcjohn463/JableDownload/blob/main/img/demo.PNG)

如果覺得好用 再麻煩給個星星好評 謝謝!!

## #####選擇性使用(Optional Use)#####

### 使用 FFmpeg 轉檔優化 : 參數能自己調(Use FFmpeg encode)

`cd ipx-486`
`ffmpeg -i ipx-486.mp4 -c:v libx264 -b:v 3M -threads 5 -preset superfast f_ipx-486.mp4`

![image](https://github.com/hcjohn463/JableDownload/blob/main/img/ff.PNG)

### 轉檔完成(Finish Encode)

![image](https://github.com/hcjohn463/JableDownload/blob/main/img/different.PNG)

### Argument parser

`$python main.py -h`

![](https://i.imgur.com/qgyS5sf.png)

`$python main.py --random True`

可以直接下載隨機熱門影片

![](https://i.imgur.com/dSsdB7Y.png)

可以直接在 cmd line 指定 url。

![](https://i.imgur.com/DKFrD7T.png)

### 更新日誌(Update log)

🏹 2023/4/19 兼容 Ubuntu Server v1.10
🦅 2023/4/15 輸入演員鏈接，下載所有該演員相關的影片 v1.9
🚗 2022/1/25 下載結束後抓封面 v1.8
🐶 2021/6/4 更改 m3u8 得到方法(正則表達式) v1.7
🌏 2021/5/28 更新代碼讓 Unix 系統(Mac,linux 等)能使用 v1.6
🍎 2021/5/27 更新爬蟲網頁方法 v1.5
🌳 2021/5/20 修改編碼問題 v1.4
🌈 2021/5/6 增加下載進度提示、修改 Crypto 問題 v1.3
⭐ 2021/5/5 更新穩定版本 v1.2

[ChromeDriver]: https://chromedriver.chromium.org/downloads
[FFmpeg]: https://www.ffmpeg.org/
