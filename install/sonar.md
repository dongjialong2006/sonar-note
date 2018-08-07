# SonarQube安装

## Mac下安装
- brew install sonar
- sonar start

## Linux下安装
- [安装JDK](http://www.cnblogs.com/owenma/p/6139860.html)
- [安装MySql](http://www.cnblogs.com/owenma/p/6394477.html)
	下载好所有的安装包之后首先配置数据库，进入数据库命令
	`mysql -u root -p
	mysql> CREATE DATABASE sonar CHARACTER SET utf8 COLLATE utf8_general_ci;
	mysql> CREATE USER 'sonar' IDENTIFIED BY 'sonar';
	mysql> GRANT ALL ON sonar.* TO 'sonar'@'%' IDENTIFIED BY 'sonar';
	mysql> GRANT ALL ON sonar.* TO 'sonar'@'localhost' IDENTIFIED BY 'sonar';
	mysql> FLUSH PRIVILEGES;`
- [安装Sonar](https://www.sonarqube.org/downloads/)
	将下载的sonarqube-7.2.zip包解压至Linux某路径如/usr/local 
- [安装Scanner](https://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner)
	将下载的sonar-scanner-cli-3.0.3.778-linux.zip包解压某路径/usr/local，同时配置环境变量
- /usr/local/sonarqube-7.2/bin/linux-x86-64/sonar.sh start 
	目录切换至sonar的/bin/linux-x86-64/目录，启动服务 
	./sonar.sh start 启动服务 
	./sonar.sh stop 停止服务 
	./sonar.sh restart 重启服务

## Docker下安装
- 获取 postgresql 的镜像:docker pull postgres
- 启动 postgresql:docker run --name db -e POSTGRES_USER=sonar -e POSTGRES_PASSWORD=sonar -d postgres
- 获取 sonarqube 的镜像:docker pull sonarqube
- 启动 sonarqube:docker run --name sq --link db -e SONARQUBE_JDBC_URL=jdbc:postgresql://db:5432/sonar -p 9000:9000 -d sonarqube

至此，sonar就安装好了 
访问http://localhost:9000, 用admin/admin登录即可。
