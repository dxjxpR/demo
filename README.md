- 根据Dockerfile文件生成镜像：docker build -t iw_preprocessing .
- 根据iw_preprocessing镜像生成容器，需要将主机中的tif目录挂载到容器中的/data目录下：docker run -itd -v tif目录:/data --name iw-preprocessing iw_preprocessingd的容器名 /bin/bash
- tif的cog创建脚本：python3 create_cog.py
- tif的缩略图创建：python3 create_thumbnails.py<br/>
  具体参数如下：<br/>&emsp;usage: start_create_thumbnails [-h] [-i INPUT] [-s OUTSIZE] [-f FORMAT] [--small] [--large]<br/>&emsp;optional arguments:<br/>&emsp;&emsp;-h, --help          show this help message and exit<br/>&emsp;&emsp;-i INPUT, --input INPUT<br/>&emsp;&emsp;&emsp;tiff路径，自动遍历子文件夹，默认为/data<br/>
   &emsp;&emsp;-s OUTSIZE, --outsize OUTSIZE<br/>
   &emsp;&emsp;&emsp; 缩略图大小，支持百分比：256,256或2%,2%<br/>
   &emsp;&emsp;-f FORMAT, --format FORMAT<br/> &emsp;&emsp;&emsp;可选：JPEG,PNG，默认：JPEG<br/>&emsp;&emsp;-p PROCESS, --process PROCESS<br/>
   &emsp;&emsp;&emsp;进程数，默认：1<br/>
- tif的影像降位：python3 uint16_to_uint8.py
