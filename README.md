# static_pic_nginx_conf

图片静态服务NGINX配置，数据量不大的时候可以当作对象存储来用。

`该repo更大的作用其实是openregestry lua demo。`

启动：

```sh
cd ~/mgnnx
WORK_DIR=$PWD PICS_DIR=/data/objs/rawimgs PORT=8087 docker-compose up -d
tail -f access.log | awk '{if ($10>0) print $1"\t"$3"\t"$6"\t"$9"\t"$10}'
```

```sh
docker run --rm -d --name nginx3 -p 8087:80
-v $PWD/config/nginx.conf:/usr/local/openresty/nginx/conf/nginx.conf:ro
-v /mnt/cephfs_online/ceph_bk_storage:/data/pics
-v $PWD/logs:/usr/local/openresty/nginx/logs
-v /etc/localtime:/etc/localtime
openresty/openresty
```
