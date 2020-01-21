# boot_from_emmc

### 

<table>
    <tr>
        <td>Foo</td>
    </tr>
</table>

    $ sudo fdisk -l
    Device         Boot  Start      End  Sectors  Size Id Type
    /dev/mmcblk0p1      204800   729087   524288  256M  c W95 FAT32 (LBA)
    /dev/mmcblk0p2      729088 14940159 14211072  6.8G 83 Linux
    
mmcblk0 是 SSD 卡<br>
mmcblk1 是 emmc<br>

    Disk /dev/mmcblk1: 7.3 GiB, 7818182656 bytes, 15269888 sectors<br>

    Device     Boot Start      End  Sectors  Size Id Type
    /dev/sda1        2048 61341695 61339648 29.3G 83 Linux

    $ cd /media
    $ sudo mkdir sda1
    $ sudo mount /dev/sda1 sda1
    $ cd sda1

    $ ls
    2019-01-08-raspbian-jessie-preview-bpi-m2z-p2z-sd-emmc.img.zip  <--- 1.8G

    $ sudo unzip -p 2019-01-08-raspbian-jessie-preview-bpi-m2z-p2z-sd-emmc.img.zip | sudo dd of=/dev/mmcblk1 bs=10M
    0+116480 records in
    0+116480 records out
    7650410496 bytes (7.7 GB, 7.1 GiB) copied, 260.784 s, 29.3 MB/s

時間大約 5 分鐘

    $ sudo fdisk -l

    Device         Boot  Start      End  Sectors  Size Id Type
    /dev/mmcblk1p1      204800   729087   524288  256M  c W95 FAT32 (LBA)
    /dev/mmcblk1p2      729088 14940159 14211072  6.8G 83 Linux

    $ sudo shutdown now

#### power off
#####    remove TF card

#### Install golang 1.13.5

    $ tar -C /usr/local -xzf go1.13.5.linux-amd64.tar.gz
