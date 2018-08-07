# 配置

## 登录
使用admin/admin登录系统

## 步骤
### 安装sonar-scanner
[sonar-scanner](https://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner)
### 创建sonar-scanner.properties
	`//项目的key
	sonar.projectKey=snc:agent
	
    //项目的名字
	sonar.projectName=snc-agent
	
    //项目的版本
    sonar.projectVersion=1.0.0
	
    //需要分析的源码的目录，多个目录用英文逗号隔开
	sonar.sources=.
	
    sonar.exclusions=**/*_test.go,**/vendor/**
	
    sonar.tests=.
    sonar.test.inclusions=**/*_test.go
	sonar.test.exclusions=**/vendor/**
	
    //覆盖率
	sonar.go.coverage.reportPaths=coverage.out
	
    //登录
	sonar.login=c2970a7d63e3a189455efa57ec31ed29996a9ed5`
### 运行sonar-Scanner
刷新http://localhost:9000即可