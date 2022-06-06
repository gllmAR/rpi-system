# kinect 2 (Kinect one)

![kinec_one](https://m.media-amazon.com/images/S/aplus-media/mg/ec801571-863a-4ed2-ab7d-b63600d8143f._SR285,285_.png)

## installation
### libfreenect2


#### edit config.txt
```
sudo nano /boot/config.txt
## search and modify the GPU-memory:
gpu_mem=64
```


#### edit cmdline.txt
```
sudo nano /boot/cmdline.txt
and modify to:
console=serial0,115200 console=tty1 root=PARTUUID=e0e69b19-02 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait quiet splash plymouth.ignore-serial-consoles usbcore.usbfs_memory_mb=64 usbcore.autosuspend=-1
```


#### install libfreenect dependencies
```
git clone https://github.com/Jyurineko/libfreenect2
sudo apt install libudev-dev
sudo apt install mesa-utils
sudo apt update
sudo apt install libgles2-mesa-dev
```


#### make libfreenect2
* -> https://github.com/OpenKinect/libfreenect2 

```
sudo apt-get install libusb-1.0-0-dev
sudo apt-get install libturbojpeg0-dev
sudo apt-get install libglfw3-dev
sudo apt-get install libopenni2-dev
mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release -DENABLE_CUDA=OFF -DENABLE_OPENCL=OFF -DENABLE_OPENGL_AS_ES31=ON -DENABLE_CXX11=ON -DENABLE_VAAPI=OFF
make -j4
```


#### Install libfreenect2

```
sudo make install
sudo ldconfig
sudo cp ../platform/linux/udev/90-kinect2.rules /etc/udev/rules.d/
```


#### Exec Protonect gl

```
./libfreenect2/build/bin/Protonect gl
```


