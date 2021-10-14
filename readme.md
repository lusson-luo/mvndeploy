jar 迁移 mvn 库例子

### 功能介绍

将一个 jar 从一个 mvn 拉取，并上传到另一个 mvn 库去。

### 文件目录

pom.xml          ---     需要上传 jar 的配置
settings.xml     ---     需要上传新 mvn 库
install/pom.xml  ---     拉取的 jar 配置
install/settings.xml     拉取的 mvn 库

### 拉取

从原 mvn 库将 jar 拉到本地。

进入 install 目录，修改 settings.xml 中账户密码，用于原 mvn 库鉴权。

```
cd install
mvn install -s settings.xml
```

### 推送

将本地 jar 上传到新 mvn 库

在当前目录下，修改 settings.xml 中的账户密码，用于新 mvn 库鉴权。

```
mvn deploy -s settings.xml
```
        