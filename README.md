# File System

## Physical Component of Hard Disk

![hard_disk](http://upload.wikimedia.org/wikipedia/commons/5/52/Hard_drive-en.svg)
![HCS](http://upload.wikimedia.org/wikipedia/commons/0/02/Cylinder_Head_Sector.svg)

- Sector: 最小的物理儲存單位，每一個 sector 為 512 bytes。
- Cylinder: 磁盤上位於同心圓的 sector 為一個 cylinder，為磁碟分割的最小單位。
- MBR (Master Boot Region): MBR 儲存在第一個 cylinder，包含 boot loader 與其他開機程序，共 446 bytes。
- Partition Table: 第一個 cylinder 用來記錄磁碟分割的資料，大小為 64 bytes，可分為主要分割與延伸分割。
- 分割類型:
  - Pirmary: 最多可以有 4 個主要分割。
  - Extension: 最多可以有 1 個延伸分割。
  - Logical: 存在于延伸分割中，可以有多個邏輯分割于一個延伸分割中。

## Ext2/3/4 File System

![file_system](http://linux.vbird.org/linux_basic/0230filesystem/ext2_filesystem.jpg)
- 為索引式檔案系統 (indexed allocation)。


## Useful Commandline Tools
