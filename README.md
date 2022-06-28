# docker
使用docker部署
1、创建harbor库
https://blog.csdn.net/zhulianseu/article/details/122696885
坑：要启动docker
systemctl start docker

2、创建tomcat docker镜像库
https://blog.csdn.net/u012586326/article/details/124434061
坑：要增加配置
vim  /etc/docker/daemon.json 

{
  "insecure-registries": ["10.250.100.159:8011"]
}

3、打包镜像：
docker commit -a "作者" -m "内容说明" 版本ID 镜像名称:版本号
标记镜像
docker tag tomcat:v1 10.250.100.159:8011/alarm/tomcat:v1
4、登录仓库
docker login 10.250.100.159:8011
5、推送镜像到镜像库
docker push 10.250.100.159:8011/alarm/tomcat:v1


常用命令：
docker images   --docker查看镜像
docker rmi -f imagesID  --docker删除镜像
systemctl restart docker   --docker 重启命令
docker ps  --docker 查看镜像运行情况
docker stop aacdafc4198f   --docker启动停止镜像运行
docker exec -it aacdafc4198f /bin/bash   --docker进入镜像环境
docker cp VehicleAlarmMonitor.war aacdafc4198ff28107fde31bfb7944b2c3ec75faad9842c3051afc5b08204b3f:/usr/local/apache-tomcat-8.5.78/webapp   --docker拷贝外部文件进docker镜像
docker run -d -p 8081:8080 镜像名称     --docker启动 8081 是外部访问的端口 8080 是tomcat自己开放端口
docker run -d -p 8081:8080 -it 镜像名称:版本  --启动已有镜像 8081 是外部访问的端口 8080 是tomcat自己开放端口





