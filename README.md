Setup môi trường 
```
sudo apt-get install raspberrypi-kernel-headers build-essential bc wget git bison flex make libssl-dev libncurses-dev
```
Sau khi setup môi trường xong di chuyển vào thư mục `linux` vừa downloads xuống từ github và chạy các lệnh sau theo từng lệnh
```
KERNEL=kernel8
sudo make bcm2712_defconfig
sudo make menuconfig
```
Build kernel
```
sudo make -j4 Image modules dtbs
```
Install drive
```
sudo make modules_install
```
Sau khi build hoàn tất copy các device và Image
```
sudo cp arch/arm/boot/dts/overlays/*.dtb* /boot/firmware/overlays
sudo cp arch/arm64/boot/Image /boot/firmware/<TềnImage>.img
```
Cuối cùng chỉnh sữa file `config.txt` 
```
sudo vim /boot/firmware/config.txt
```
Thêm vào dòng cuối `[all]`: `kernel=<TềnImage>.img`


