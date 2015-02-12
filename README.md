# File System

## Physical Component of Hard Disk

![hard_disk](http://upload.wikimedia.org/wikipedia/commons/5/52/Hard_drive-en.svg)
![HCS](http://upload.wikimedia.org/wikipedia/commons/0/02/Cylinder_Head_Sector.svg)

- Sector: 最小的物理儲存單位，每一個 sector 為 512 bytes。
- Cylinder: 磁盤上位於同心圓的 sector 為一個 cylinder，為磁碟分割的最小單位。
- MBR (Master Boot Region): MBR 儲存在第一個 cylinder，包含 boot loader 與其他開機程序，共 446 bytes。
- Partition Table: 位於第一個 cylinder 用來記錄磁碟分割的資料，大小為 64 bytes，可分為主要分割與延伸分割。
- 分割類型:
  - Pirmary: 最多可以有 4 個主要分割。
  - Extension: 最多可以有 1 個延伸分割。
  - Logical: 存在于延伸分割中，可以有多個邏輯分割于一個延伸分割中。

## Ext2/3/4 File System

(圖片截自: <a href="http://linux.vbird.org/linux_basic/0230filesystem.php#harddisk-inode">鳥哥的私房菜</a>)
![file_system](http://linux.vbird.org/linux_basic/0230filesystem/ext2_filesystem.jpg)
- 為索引式檔案系統 (indexed allocation)。
- Ext2 是以 block group 來管理整個 file system，每一個 block group 由下列幾個部分組成:
  - Superblock (1024 bytes) 包含:
	- block 與 inode 的總量。
  	- 未使用與已使用的 inode / block 的數量。
  	- block 與 inode 的大小。
  	- 掛載、最後一次寫入、最後一次檢驗磁碟時間。
  	- valid bit。(0 為未掛載、1 為已掛載)
  - Inode table 包含(一個 inode 對應一個檔案):
  	- 每個檔案的 r/w/x mode。
  	- 擁有者與群組資訊。
  	- 容量。
  	- ctime、atime、mtime
  	- flags。(suid, guid...etc)
  	- pointer。
  - Data block: Ext2 支援 1K、2K 與 4K 三種 block size。
  - File System Description: 記錄 block group 開始與結束的 block 號碼還有 superblock、bitmap、inodemap、data block 的 block 起始終結號碼。(可用 dumpe2fs 查看)
  - Block bitmap: 記錄每個 block 對應的號碼與其 block 的使用狀態。
  - Inode bitmap: 記錄每個 inode 的使用狀態。

## Useful Commandline Tools

- dumpe2fs [-bh] 裝置名
  - -b: 列出保留為壞軌的部分。
  - -h: 僅列 superblock 的資訊。