# PocketsphinxRealization

## CMU Pocketsphinx 环境搭配：
需要的库：<br>gcc, automake, autoconf, libtool, bison, swig,(apt-get安装)<br>pulseaudio包(官网)<br>pocketsphinx下载：（库中有）[点击下载](https://sourceforge.net/projects/cmusphinx/files/pocketsphinx/5prealpha/pocketsphinx-5prealpha.tar.gz/download)<br>### 文档：<br>https://cmusphinx.github.io/doc/pocketsphinx/index.html<br>sphinxbase下载：[点击下载](https://sourceforge.net/projects/cmusphinx/files/sphinxbase/5prealpha/sphinxbase-5prealpha.tar.gz/download)<br>Sphinxbase安装:<br>执行下列命令<br>
```
tar -xzvf sphinxbase-5prealpha.tar.gz
cd sphinxbase-5prealpha
./autogen.sh
./configure
sudo make
sudo make install
```
链接：
```
sudo gedit /etc/ld.so.conf
```
添加下列两行
```
export LD_LIBRARY_PATH=/usr/local/lib
export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig
```
Pocketsphinx 安装：
```
tar -xzvf pocketsphinx-5prealpha.tar.gz
cd pocketsphinx-5prealpha
./configure
sudo make
sudo make install
```
## DEMO实现
参数修改:<br>在DEMO文件夹下编辑argpath文件：<br>默认为：<br>-hmm zh_broadcastnews_ptm256_8000 -lm zh_broadcastnews_64000_utf8.DMP -dict zh_broadcastnews_utf8.dic -inmic yes -time yes<br>前三个参数依次为声学模型文件夹、语言模型、字典，可以使用绝对地址<br>-inmic 可替换为 -infile <.wav>以用于输入文件识别<br>-time可设置为no以屏蔽时间显示。<br><br>编译:<br>在DEMO文件夹下编译：
```
sudo gcc -o ReadFromMic DEMO.c     -DMODELDIR=\"`pkg-config --variable=modeldir pocketsphinx`\"     `pkg-config --cflags --libs pocketsphinx sphinxbase`
```
预训练模型在model文件夹中存有
