
vi / vim 有三種模式

- 一般模式: 開啓 vim 時最初進入的模式，可以使用『刪除字元』、『刪除整行』與『複製、貼上』來處理你的文件資料。
- 編輯模式:
  - i, a: Insert mode
  - R: Replace mode
- 指令列命令模式: 提供讀取、存檔、大量取代字元、離開 vi 、顯示行號等等的動作

![vbird_vim](http://linux.vbird.org/linux_basic/0310vi//vi-mode.gif) <br>
(圖片來源: <a href="http://linux.vbird.org/linux_basic/0310vi.php">鳥哥的 Linux 私房菜</a>)

**可以到 https://github.com/amix/vimrc 找到超炫的 vim 版本喔!**

## 一般模式常用指令

`<command>` --> 為超常用指令，優先背!

### 游標移動

- `[Ctrl]+[f]`: 螢幕『向下』移動一頁，相當於 [Page Down]按鍵 (f for forward)
- `[Ctrl]+[d]`: 螢幕『向下』移動半頁 (d for down)
- `[Ctrl]+[u]`: 螢幕『向上』移動半頁 (u for up)
- +: 移動到下一列
- -: 移動到上一列
- n<space>: 向後面移動 n 個字元距離
- `0`: 移動到這一行的最前面字元處
- `$`: 移動到這一行的最後面字元處
- H: 移動到這個螢幕的最上方那一行的第一個字元 (H for home)
- M: 移動到這個螢幕的中央那一行的第一個字元 (M for middle)
- L: 游標移動到這個螢幕的最下方那一行的第一個字元 (L for left)
- `G`: 移動到這個檔案的最後一行
- `nG`: 移動到這個檔案的第 n 行
- `gg`: 移動到這個檔案的第一行
- `n<Enter>`: 游標向下移動 n 行
### 搜尋 / 取代字元

- `/word`: 向游標之下尋找一個名稱為 word 的字串
- `?word`: 向游標之上尋找一個字串名稱為 word 的字串
- `n`: 重複前一個搜尋的動作
- `N`: 反向進行前一個搜尋
- `:n1,n2s/word1/word2/g`: 在第 n1 與 n2 行之間尋找 word1 這個字串，並將該字串取代為 word2 
- `:n1,$s/word1/word2/g`: 從第一行到最後一行尋找 word1 字串，並將該字串取代為 word2
- `:n1,n2s/word1/word2/gc`: 取代前顯示提示字元給使用者確認 (confirm)

### 刪除 / 複製 / 貼上

- `x,X`: x 為向後刪除一個字元，X 為向前刪除一個字元
- nx: 連續向後刪除 n 個字元
- `dd`: 刪除游標所在的那一整列
- `u`: 復原前一個動作
- `[Ctrl]+r`: 重做上一個動作
- `ndd`: 刪除游標所在的向下 n 列
- d1G: 刪除游標所在到第一行的所有資料 
- dG: 刪除游標所在到最後一行的所有資料
- d$: 刪除游標所在處，到該行的最後一個字元
- d0: 刪除游標所在處，到該行的最前面一個字元
- `yy`: 複製游標所在的那一行
- `nyy`: 複製游標所在的向下 n 列
- y1G: 複製游標所在列到第一列的所有資料
- yG: 複製游標所在列到最後一列的所有資料
- y0: 複製游標所在的那個字元到該行行首的所有資料
- y$: 複製游標所在的那個字元到該行行尾的所有資料
- `p,P`: p 為將已複製的資料在游標下一行貼上，P 則為貼在游標上一行
- J: 將游標所在列與下一列的資料結合成同一列
- c: 刪除多行；例如 10cj = 向下刪除 10 行，10ck = 向上刪除 10 行
- .: 重複前一個動作的意思

### 模式切換

- `i,I`: 插入模式 (Insert mode)，i 為『從目前游標所在處插入』，I 為『在目前所在行的第一個非空白字元處開始插入』
- a,A: 插入模式 (Insert mode)，a 為『從目前游標所在的下一個字元處開始插入』，A 為『從游標所在行的最後一個字元處開始插入』
- o,O: 插入模式(Insert mode)，o 為『在目前游標所在的下一行處插入新的一行』； O 為在目前游標所在處的上一行插入新的一行
- r,R: 取代模式 (Replace mode)，r 只會取代游標所在的那一個字元一次；R會一直取代游標所在的文字，直到按下 ESC 為止

### 指令列指令

- `:w`
- `:q`
- `:<command>!`:
- ZZ
- :w <filename>:
- `:r <filename>`:
- :n1,n2 w [filename]:
- `:! command`: 似 ipython 中的 ! command，可查看此時在 shell 執行指令的結果會如何。ex :! ls

### 暫時性改變 vim 環境

- `:set [setting]`: 例如 :set nu 為顯示行數； :set nonu 為不顯示行數

### vim 環境設定

**set:**

- nu / nonu: 開啟/取消顯示行號
- hlsearch / nohlsearch: 開啟/取消搜索反白
- autoindent / noautoindent: 開啟 / 取消自動縮排
- backup: 自動備份
- ruler: 顯示 ruler
- bg=dark/light: 設定背景色調
- backspace=[012]: 0 or 1 --> 不許 backspace 刪除字元；2 --> 允許 backspace 刪除字元

**不用 set:**

- syntax on / syntax off: 開啟/取消語法檢查


## 編碼轉換

- `iconv` \# 轉換編碼
  - --list: 列出所有 iconv 支援的編碼
  - -f: from
  - -t: to
  - -o: output file

ex: iconv -f big5 -t utf8 test.txt -o test.utf8

