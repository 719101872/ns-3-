###此记录是ubuntu18.04安装ns-3的过程
####安装依赖，[点这里](https://www.nsnam.org/docs/release/3.30/tutorial/singlehtml/index.html#getting-started)按照官网安装ns-3的依赖（部分依赖没有安装上，有的是包名更改了，有的是没有了，这里不做记录，因为这些依赖主要提供ns-3额外的功能，这里没有做对应测试，如果在之后的使用中需要此功能可以安装依赖重新编译）  
####下载ns-3.30安装包  
`wget http://www.nsnam.org/release/ns-allinone-3.30.tar.bz2`  
####解压安装包
`tar xjf ns-allinone-3.30.tar.bz2`  
#### ns-allinone-3.30 文件下ns-3编译(ns-3编译4BG内存是不够使用的，我提供的是8gb内存，而且需要提供足够的存储空间)
`sudo ./build.py --enable-examples --enable-tests`  
![编译结果](image/1.png)  
###测试videostream  
`git clone https://github.com/guoxiliu/VideoStream-NS3.git`
####将VideoStream-NS3目录中的scratch,src的文件拷贝到ns-allinone-3.30中的ns-3.30目录中的对应目录中
####重新编译ns-3（在除第一次编译后续的编译都是使用此命令）
在ns-3.30目录下执行
`sudo ./waf clean`  
`sudo ./waf`  
最后结果养龟与上附图一致  
####代码测试  
在ns-3.30目录执行
`sudo ./waf --run videoStreamer`
得到如下结果  
![编译结果](image/ns-3_100m_video.png) 
在设置videoStreamTest.cc中带宽为2mb之后再重新编译并执行
`sudo ./waf --run videoStreamer`后可以看到
![编译结果](image/ns-3_2m_video1.png) 
