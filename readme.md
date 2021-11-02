jar 迁移 mvn 库例子

### 功能介绍

将一个 jar 从一个 mvn 拉取，并上传到另一个 mvn 库去。

### 文件目录

settings.xml     ---     需要上传新 mvn 库 \
install/pom.xml  ---     拉取的 jar 配置 \
install/settings.xml     拉取的 mvn 库

### 拉取

从原 mvn 库将 jar 拉到本地。

进入 install 目录，修改 settings.xml 中账户密码，用于原 mvn 库鉴权。

```
cd install
mvn install -s settings.xml
```

### 推送

将上传 jar 从 ~/.m2/xx/xx 拖动到当前文件夹下，执行
```
mvn deploy:deploy-file -DgroupId=net.coding.common \ # jar 的 groupId
  -DartifactId=tracing \ # jar 的 artifactId
  -Dversion=5.0.3.trace.pro.beta \ # jar 的 version
  -Dpackaging=jar \
  -Dfile=tracing-5.0.3.trace.pro.jar \ # jar 文件路径
  -DrepositoryId=devops-registry-maven-release \ # setting 中的包含用户密码的远程库 id
  -Durl=https://xx.net/repository/registry/maven-release \ # mvn 库地址
  -s settings.xml
```

参考：
1. https://maven.apache.org/guides/mini/guide-3rd-party-jars-remote.html
2. http://maven.apache.org/plugins/maven-deploy-plugin/deploy-file-mojo.html
