- Go to installation location &  Download ffmpeg

\

cd /usr/local/ wget https://ffmpeg.org/releases/ffmpeg-4.0.2.tar.bz2

\

- Untar  and give permission\
  \

tar -xf ffmpeg-4.0.2.tar.bz2 chmod -R 755 ffmpeg-4.0.2 chown -R
dhtv-prod:newshunt-tech ffmpeg-4.0.2

\

- Configure with required module\
  \

./configure \--enable-gpl \--enable-version3 \--enable-static
\--enable-libx264 \--enable-libfdk_aac \--enable-nonfree
\--prefix=/usr/local/ffmpeg-4.0.2 Make clean Make Make install

\

- Add the path in profile

\

vi /etc/profile.d/jdk.sh /usr/local/ffmpeg-4.0.2/bin/

\

 

**[Issue Faced while the Installation]{.underline}**

1.  ERROR: libfdk_aac not found

 

**              Resolution**

Find the config path and export

\

export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig

\

"/opt/ffmpeg_build/lib/pkgconfig/fdk-aac.pc"

\

       2. \[libavcodec/libfdk-aacenc.o\] Error 1

\

libavcodec/libfdk-aacenc.c: In function 'aac_encode_init':

libavcodec/libfdk-aacenc.c:292: error: 'AACENC_InfoStruct' has no member
named 'encoderDelay'

make: \*\*\* \[libavcodec/libfdk-aacenc.o\] Error 1

**                Resolution**

Complied fdk-aac from below link

<http://www.linuxfromscratch.org/blfs/view/8.3/multimedia/ffmpeg.html>

<http://www.linuxfromscratch.org/blfs/view/8.3/multimedia/fdk-aac.html>

\

[     
3. ]{style="letter-spacing: 0.0px;"}[libfdk-aac.so](http://libfdk-aac.so){style="letter-spacing: 0.0px;"}[.1:
cannot open]{style="letter-spacing: 0.0px;"}

\

\# /usr/local/ffmpeg-4.0.2/ffmpeg

/usr/local/ffmpeg-4.0.2/ffmpeg: error while loading shared libraries:
[libfdk-aac.so](http://libfdk-aac.so).1: cannot open shared object file:
No such file or directory

**                Resolution         **

Change the lib location below and update.

\

/etc/ld.so.conf ldconfig

\

\

**-Sanal K**
