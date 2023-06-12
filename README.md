为了便于阅读源码学习, 在master分支基础上创建learn分支. 
作出以下修改, 最终表现为一个linux平台下epoll实现的tcp层协议代理:
1) 整理项目结构, 将头文件和源文件分开存放
2) 将src/core/nginx.c移到项目根目录
3) 删除misc, mail, http, os/win32, event/quic这些目录
4) 删除os/unix中非linux平台代码, 以及aio, gcc代码
5) 删除event/modules中非epoll代码
6) 删除event目录中ngx_event_acceptex.c, ngx_event_connectex.c
   删除stream目录中ngx_stream_geoip_module.c
7) 修改conf/nginx.conf配置文件
8) 格式化项目代码


编译前在项目根目录执行以下命令
./auto/configure --prefix=. --with-threads --with-stream --with-stream_ssl_module --with-pcre --without-http

运行
./bin/nginx
