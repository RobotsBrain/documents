#编译

从`github`上下载源码：
```
$ git clone https://github.com/j0sh/crtmpserver.git
```

编译：
```
$ cd crtmpserver/
$ sh cleanup.sh 
$ cd builders/cmake
$ cmake .
$ make
```


#运行

启动`rtmp`服务：
```
$ ./crtmpserver/crtmpserver ./crtmpserver/crtmpserver.lua
```

向`rtmp`服务器推流：
``` 
$ ffmpeg -re -i test.flv -vcodec copy -acodec copy -f flv -y rtmp://localhost:1935/live/livestream
```

播放视频：
```
$ ffplay rtmp://localhost:1935/live/livestream
```


#配置

如果服务器对某些端口需要做限制，就需要自己指定端口。这个需求可以通过修改它的配置脚本`crtmpserver/crtmpserver.lua`来实现。