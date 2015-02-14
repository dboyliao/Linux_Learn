# Vi and Vim

vi / vim 有三種模式

- 一般模式: 開啓 vim 時最初進入的模式，可以使用『刪除字元』、『刪除整行』與『複製、貼上』來處理你的文件資料。
- 編輯模式:
  - i, a: Insert mode
  - R: Replace mode
- 指令列命令模式: 提供讀取、存檔、大量取代字元、離開 vi 、顯示行號等等的動作

![vbird_vim](http://linux.vbird.org/linux_basic/0310vi//vi-mode.gif)

## 一般模式常用指令

### 游標移動

- `[Ctrl]+[f]`: 螢幕『向下』移動一頁，相當於 [Page Down]按鍵 (f for forward)
- `[Ctrl]+[b]`: 螢幕『向上』移動一頁，相當於 [Page Up] 按鍵 (b for backward)
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

- /word:
- ?word:
- n:
- N:
- `:n1,n2s/word1/word2/g`:
- `:n1,$s/word1/word2/g`:
- `:n1,n2s/word1/word2/gc`:

