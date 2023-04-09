# s3 mount on ec2 using s3fs

1.
```
sudo yum update -y
```
2.
```
sudo yum install automake fuse fuse-devel gcc-c++ git libcurl-devel libxml2-devel make openssl-devel
```
3.
```
git clone https://github.com/s3fs-fuse/s3fs-fuse.git
```
4.
```
cd  s3fs-fuse
# ./autogen.sh 
# ./configure --prefix=/usr --with-openssl
# make 
# make install
```
5.
```
which s3fs
```
6.
Create role s3full and attach to ec2 \
create vi /root/.passwd-s3fs \
accesskey:secretkey /
set 600 file permission
7.
```
mkdir /root/mys3dir
```
8.
```
s3fs mubucket /mys3dir -o passwd_file=/root/.passwd-s3fs```
9.
df -Th

