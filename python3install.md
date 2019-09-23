操作系统环境
```
cat /etc/redhat-release
CentOS Linux release 7.6.1810 (Core)
```

安装依赖包
```
yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel  libffi-devel gcc make gdbm-devel db4-devel libpcap-devel xz-devel yum-utils
```

下载&解压缩
```
curl -O https://www.python.org/ftp/python/3.7.4/Python-3.7.4.tgz
tar -zxvf Python-3.7.4.tgz
```

编译安装Python3.7
```
cd /root/Python-3.7.4
./configure prefix=/usr/local/python3

./configure prefix=/usr/local/python3 --enable-optimizations 对性能有10%的优化，但是会增加编译时间

make && make install
```

备份软链接
```
mv /usr/bin/python /usr/bin/python.backup
```

调整python&pip软链接
```
sudo ln -s /usr/local/python3/bin/python3.7 /usr/bin/python3
sudo ln -s /usr/bin/python3 /usr/bin/python
sudo ln -s /usr/local/python3/bin/pip3.7 /usr/bin/pip3
sudo ln -s /usr/bin/pip3 /usr/bin/pip
```

修改yum的python版本
```
sudo sed -i "s/#\!\/usr\/bin\/python/#\!\/usr\/bin\/python2/g" /usr/bin/yum
sudo sed -i "s/#\! \/usr\/bin\/python/#\! \/usr\/bin\/python2/g" /usr/libexec/urlgrabber-ext-down
sudo sed -i "s/#\! \/usr\/bin\/python/#\! \/usr\/bin\/python2/g" /usr/bin/yum-config-manager
```

更新pip命令
```
pip install --upgrade pip
```


验证安装后的版本
```
python -V && pip -V
```
