# docker
<hr/>
## 使用docker部署 <br/>
1、创建harbor库 <br/>
https://blog.csdn.net/zhulianseu/article/details/122696885 <br/>
坑：要启动docker <br/>
systemctl start docker <br/>

2、创建tomcat docker镜像库 <br/>
https://blog.csdn.net/u012586326/article/details/124434061 <br/>
坑：要增加配置 <br/>
vim  /etc/docker/daemon.json  <br/>

{ <br/>
  "insecure-registries": ["10.250.100.159:8011"] <br/>
} <br/>

3、打包镜像： <br/>
docker commit -a "作者" -m "内容说明" 版本ID 镜像名称:版本号 <br/>
标记镜像 <br/>
docker tag tomcat:v1 10.250.100.159:8011/alarm/tomcat:v1 <br/>
4、登录仓库 <br/>
docker login 10.250.100.159:8011 <br/>
5、推送镜像到镜像库 <br/>
docker push 10.250.100.159:8011/alarm/tomcat:v1 <br/>

<hr/>
常用命令： <br/>
docker images   --docker查看镜像 <br/>
docker rmi -f imagesID  --docker删除镜像 <br/>
systemctl restart docker   --docker 重启命令 <br/>
docker ps  --docker 查看镜像运行情况 <br/>
docker stop aacdafc4198f   --docker启动停止镜像运行 <br/>
docker exec -it aacdafc4198f /bin/bash   --docker进入镜像环境 <br/>
docker cp VehicleAlarmMonitor.war aacdafc4198ff28107fde31bfb7944b2c3ec75faad9842c3051afc5b08204b3f:/usr/local/apache-tomcat-8.5.78/webapp   --docker拷贝外部文件进docker镜像 <br/>
docker run -d -p 8081:8080 镜像名称     --docker启动 8081 是外部访问的端口 8080 是tomcat自己开放端口 <br/>
docker run -d -p 8081:8080 -it 镜像名称:版本  --启动已有镜像 8081 是外部访问的端口 8080 是tomcat自己开放端口 <br/>





