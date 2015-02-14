# Compress Files

## 檔案備份

常見 Linux 壓縮工具: compress、gzip、zcat、bzip2、bzcat 與 tar
(compress 過於老舊，故略過)

- `gzip [-cdtv#] 檔名` \# 壓縮檔案
  - -c: 把壓縮出的檔案以 stdout 輸出。
  - -d: 解壓縮。
  - -t: 查看壓縮有無錯誤。
  - -v: 顯示壓縮比等資訊。
  - -#: # 可以是 1~9，1 最快但壓縮比差，9 最慢但壓縮比好。

note: `gzip` 壓縮完會取代原檔案。 <br>
ex: `gzip -c -9 test.txt > test.gz` \# 不取代原檔案的做法


- `zcat xxx.gz` \# 再不解壓縮的情況下把內容 cat 出來。
(可用於解壓縮完為文字檔的壓縮檔)

- `bzip2 [-cdkzv#] 檔名` \# bzip2 壓縮比比 gzip 好。
  - -c: 同 gzip
  - -d: 同 gzip
  - -k: 保留原檔案。
  - -z: 壓縮。
  - -v: 同 gzip
  - -#: 同 gzip 

ex: `bzip2 -z -9 -k test.txt` \# 壓縮 test.txt <br>
ex: `bzip2 -d test.txt.bz2` \# 解壓縮 test.txt.bz2 <br>

## 資料夾/檔案備份

- `tar` \# 參數超多....請見說明
  - -c: 執行壓縮
  - -x: 執行解壓縮
  - -t: 查看壓縮檔
  - -j: 以 bzip2 壓縮
  - -z: 以 gzip 壓縮
  - -v: 顯示進度
  - -f filename: 壓縮檔名稱 
  - -C directory: 解壓縮至特定資料夾
  - -p: 保留原始檔案權限
  - -P: 保留絕對路徑 --> 解壓縮時會以絕對路徑解壓縮
  - -O: stdout 輸出。
  - --exclude=PATTERN: 排除所有符合 PATTERN 的檔名。

note: 使用 -j/-z 時，副檔名最好是 tar.bz2/tar.gz 。<br>
note: -c -x -t 不可同時出現。<br>
note: 保留絕對路徑解壓縮時會把原本電腦的檔案蓋掉。<br>
note: `tar -xjv -f xxx.tar.bz2 filename` 將只解壓縮 xxx.tar.bz2 中的 filename 。<br>
note: `tar -xjv -f xxx.tar.bz2` 將解壓縮所有檔案。<br>
note: 可以有多個 `--exclude`。例如: `--exclude=PATTERN1 --exclude=PATTERN2`。

## 完整檔案系統備份

- `dump [-Suvj] [-level] [-f 備份檔名] 欲備份的資料` \# 可用於備份單一資料夾或完整檔案系統
  - -S: 列出 dump 所需空間
  - -u: 將 dump 的時間記錄至 /etc/dumpdates 中 (只支援備份檔案系統時)
  - -v: 同 bzip2 等備份指令之 -v
  - -j: 以 bzip2 支援備份
  - -f: 同 bzip2 等備份指令之 -f
  - -level: dump 等級，由 0 ~ 9 (見下圖)
  - -W: 查看所有在 /etc/fstab 中的檔案系統是否有被 dump 過 

![vbird_dump](http://linux.vbird.org/linux_basic/0240tarcompress//dump-1.gif)
(圖片截自 <a href="http://linux.vbird.org/linux_basic/0240tarcompress.php#dump_restore">鳥哥的 Linux 私房菜</a>)

- `restore` \# 與 dump 對應，用以回復資料或整個檔案系統
  - mode options: (不可混用)
    - -t: 查看 dump 下來的檔案內容。似 tar -t
    - -C: 把 dump 中的檔案與實際檔案系統做比較。似 git diff
    - -i: 互動模式
    - -r: 還原整個檔案系統
  - general options: (配合各種 mode 使用)
    - -h: 查看 dump 的 inode 與 label 等資訊
    - -f filename.dump: 欲處理的 dump file 。 
    - -D mount_point: 可與 -C 混用，可比較 dump 內容與目標掛載點的差別。 

## 其他常用工具

