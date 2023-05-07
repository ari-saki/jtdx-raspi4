# jtdx-raspi4
install jtdx for raspberrypi4(bullseye)

## 1.package install

https://github.com/jtdx-project/jtdx/blob/master/INSTALL

```
sudo apt-get update
sudo apt-get install -y git
sudo apt-get install -y cmake
sudo apt-get install -y automake
sudo apt-get install -y libtool
sudo apt-get install -y asciidoctor
sudo apt-get install -y asciidoc
sudo apt-get install -y gfortran
sudo apt-get install -y subversion
sudo apt-get install -y libwxgtk3.0-dev
sudo apt-get install -y libusb-1.0-0-dev
sudo apt-get install -y portaudio19-dev
sudo apt-get install -y libsamplerate0-dev
sudo apt-get install -y libasound2-dev
sudo apt-get install -y libao-dev
sudo apt-get install -y libfftw3-dev
sudo apt-get install -y libgsm1-dev
sudo apt-get install -y libjpeg9-dev
sudo apt-get install -y libxft-dev
sudo apt-get install -y libxinerama-dev
sudo apt-get install -y libxcursor-dev
sudo apt-get install -y libboost-all-dev
sudo apt-get install -y libqt5multimedia5
sudo apt-get install -y libqt5multimedia5-plugins
sudo apt-get install -y libqt5multimediawidgets5
sudo apt-get install -y libqt5serialport5-dev
sudo apt-get install -y libqt5svg5-dev
sudo apt-get install -y libqt5widgets5
sudo apt-get install -y libqt5sql5-sqlite
sudo apt-get install -y libqwt-qt5-dev
sudo apt-get install -y libsndfile1-dev
sudo apt-get install -y libudev-dev
sudo apt-get install -y qtmultimedia5-dev
sudo apt-get install -y texinfo
sudo apt-get install -y xsltproc
sudo apt-get install -y swig
sudo apt-get install -y qttools5-dev
sudo apt-get install -y qttools5-dev-tools
sudo apt-get install -y qtbase5-dev-tools
sudo apt-get install -y libqt5websockets5-dev
```

## 2.build hamlib

https://github.com/jtdx-project/jtdx/blob/master/INSTALL

```
$ mkdir ~/hamlib-prefix
$ cd ~/hamlib-prefix
$ git clone git://git.code.sf.net/p/jtdx/hamlib src
$ cd src
$ ./bootstrap
$ mkdir ../build
$ cd ../build
$ ../src/configure --prefix=$HOME/hamlib-prefix \
   --disable-static --enable-shared --without-readline \
   --without-indi --without-cxx-binding --disable-winradio \
   CFLAGS="-g -O2 -fdata-sections -ffunction-sections" \
   LDFLAGS="-Wl,--gc-sections"
$ make
$ make install-strip
```

## 3.build jtdx

https://jtdx.freeforums.net/thread/124/raspberry-pi-4-400-installation

https://github.com/jtdx-project/jtdx/blob/master/INSTALL

```
$ mkdir -p ~/jtdx-prefix/build
$ cd ~/jtdx-prefix
$ git clone git://git.code.sf.net/p/jtdx/code src
$ cd ~/jtdx-prefix/build
$ cmake -D CMAKE_INSTALL_PREFIX=~/jtdx-install -D CMAKE_PREFIX_PATH=~/hamlib-prefix ../src
$ cmake --build .
$ cmake --build . --target install
```


## 4.run
```
$ cd ~/jtdx-install/bin
$ ./jtdx
```
