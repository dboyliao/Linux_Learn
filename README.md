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

note: `gzip` 壓縮完會取代原檔案。
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

ex: `bzip2 -z -9 -k test.txt` \# 壓縮 test.txt
ex: `bzip2 -d test.txt.bz2` \# 解壓縮 test.txt.bz2

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

note: 使用 -j/-z 時，副檔名最好是 tar.bz2/tar.gz 。
note: -c -x -t 不可同時出現。
note: 保留絕對路徑解壓縮時會把原本電腦的檔案蓋掉。
note: `tar -xjv -f xxx.tar.bz2 filename` 將只解壓縮 xxx.tar.bz2 中的 filename 。
note: `tar -xjv -f xxx.tar.bz2` 將解壓縮所有檔案。
note: 可以有多個 `--exclude`。例如: `--exclude=PATTERN1 --exclude=PATTERN2`。



