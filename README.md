# WhiskyWine 使用教學

## 使用步驟

### 1. 安裝 Homebrew

透過 `Terminal (終端機)` 安裝 `Homebrew`。安裝完成後，會顯示 `Installation successfl` 字樣

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
![](https://imgur.com/eE7H70W.jpeg)
![](https://imgur.com/AOYWccB.jpg)

### 2. 安裝 WhiskyWine

```sh
brew install --cask --no-quarantine gcenx/wine/wineskin
```
![](https://imgur.com/Rdit9DZ.jpeg)

安裝完成後，即可從啟動台 LaunchPad 看到 `Wineskin Winery`，或是直接到 `Applicatino (應用程式) ` 查看。
![](https://imgur.com/m8D9nxT.jpeg)
打開 `Wineskin Winery`，取得最新 Wrapper 和 Engine。

- Wrapper: 相當於遊戲的啟動環境
- Engine: 為支撐環境所需要的工具

![](https://imgur.com/Vxg43sr.jpeg)

新裝的情況下，會直接請你安裝 `Wrapper`， `Engine` 部分可以直接採用最新版或是相對穩定的版本即可。我這邊採用的是 `WS12WineCX64Bit23.7.1-cnc-ddraw_6.6.0.0`

![](https://imgur.com/ZbACeYV.jpeg)

### 3. 安裝 PC 軟體或遊戲

輸入任意名稱後，建立會花一些時間，約幾分鐘的時間。

![](https://imgur.com/jq0cYrY.jpeg)

建立完成後，會看到下面畫面，打開資料匣瀏覽，或是到其路徑 `/User/<你的使用者名稱>/Applications/Wineskin/`，或是到啟動台，會看到剛剛建立的 `test` Wrapper。
![](https://imgur.com/9AD5zXR.jpeg)![](https://imgur.com/dT3UB5J.jpeg)

打開後，會看到下面畫面，點擊第一個 `Install Software` 安裝要使用的軟體。
![](https://imgur.com/tKNYoaV.jpeg)
如果是安裝檔 `EXE` 選第一個，免安裝檔則是用下方 `Copy a Folder inside` 或 `Move a Folder inside`。
![](https://imgur.com/H1bUKuB.jpeg)

這邊測試使用的是 `Steam` Windows 版安裝，安裝步驟則跟一般相同，這邊就不多贅述。
> 如果啟動卡太久沒出現，可以直接關掉重啟。

![](https://imgur.com/GAc4xbC.jpeg)

## 問題排除
### 設定啟動路徑

因為 `Wineskin` 裝完，預設是空的啟動路徑，所以可以選擇想啟動的路徑，直接點擊打開即可。
採用上面建立的例子，打開 `test` Wrapper 看到下方畫面，點擊第三個 `Advanced`。
![](https://imgur.com/tKNYoaV.jpeg)
會出現下方畫面，選擇要啟動的軟體，例如我這邊選擇 Steam app
![](https://imgur.com/jun52am.jpeg)
![](https://imgur.com/fyB5RSw.jpeg)
> 遇到畫面卡住，可以試著把下方 `Direct3D to Metal translation layer - (D3DMetal/GPTK)` 打勾，或許就可以解決，如果還是不行，可能就要等工具修正了。

如果之後要修改啟動路徑需要從 Wineskin 資料匣內選擇 `顯示套件內容` 進入 app 資料匣裡面的 `Wineskin` 進行修改，看到畫面同上步驟。
![](https://imgur.com/ICFEw9f.jpeg)
![](https://imgur.com/ZBhpMhR.jpeg)
 
> 目前測試，使用的到工具和軟體，大部分都可以打開：Steam, Battle.Net, 壓縮軟體等等
> 但還是需要再次提醒，目前不是所有 Windows 軟體都可以運行，相關內容在其官方文檔的常見問題
> 說明如下：
> 
>   * 遊戲因“指令無效”而崩潰：您的遊戲可能正在使用 AVX 指令。這些在控制台端口中更為常見。AVX 指令是特定於 x86 的，Rosetta 不會翻譯它們。除非你能找到一種方法來禁用或繞過它們（在線檢查），否則你的遊戲將無法運行。
>   * 無法加載某些競爭激烈的多人遊戲：競爭性多人遊戲，尤其是大逃殺和其他 FPS 遊戲（如 PUBG、Fortnite、Apex Legends、Valorant），通常具有某種形式的驅動程序級反作弊。這些在 Wine 下不起作用。
> 
> 如果有其它問題，可以在其官方 Github 提 issue：https://github.com/Whisky-App/Whisky


### 中文亂碼問題

把常見字體放到 `/Users/<你的名稱>/Applications/Wineskin/<你的APP>/Contents/SharedSupport/prefix/drive_c/windows/Fonts`內即可，或是直接使用下方提供的字體。

字體文件： [SIMSUN.TTC](https://lanyundev.com/download_file/%E6%9D%82%E9%A1%B9/%E5%AD%97%E4%BD%93/SIMSUN.TTC)
![](https://imgur.com/l9YsUn9.jpeg)

> 另外一種較為複製的做法，可以參考 [如何調校 macOS 上的 Wine 解決中日文亂碼？以 Whisky 為例](https://becoder.org/macos-wine-tuning/)，其中做法為用中文字體直接改變原有會遇到的常見字體，便於無需選擇字體。

### 登入窗口打不開問題

目前測試，只要多開幾次即可

### 字體模糊問題

如果是使用 MBP，其螢幕為 Retina 螢幕，而 Wine 沒有真實解析度，故字體模糊。

解決方法是打開註冊表編輯器 (Registry Editor （regedit）)
![](https://imgur.com/FnpDsGA.jpeg)
在 `HKEY_CURRENT_USER\Software\Wine\Mac Driver` 中加入 `RetinaMode` 的字串值，並將值編輯為 `Y`。
![](https://imgur.com/a4uCobv.jpeg)

由於啟動了 `RetinaMode`，窗口畫面會變很小，建議根據實際情況調整 DPI 解析度。
從 `Tools` 的 `Config Utility (winecig)` 進入。
![](https://imgur.com/a4uCobv.jpeg)
![](https://imgur.com/wJmkUBR.jpeg)

### Wineskin app 改變存放位置

到路徑 `/User/<你的使用者名稱>/Applications/Wineskin/`找到目前使用的 Wrapper 環境，
由於友善的封裝為一個檔案，故直接把整個檔案搬移到你想要的目錄即可。

