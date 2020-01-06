## maven-repo
   通过一番尝试，得出的一个能极简设置，使用github做maven私仓标准项目。
   
   该项目也是个人准备用作私仓。
   
   
## 1、发布jar到项目下的本地路径：

首先，需要修改deploy插件的配置：
```xml
<plugin>
	<groupId>org.apache.maven.plugins</groupId>
	<artifactId>maven-deploy-plugin</artifactId>
	<version>2.8.2</version>
	<configuration>
		<packaging>jar</packaging>
		<groupId>oracle</groupId>
		<artifactId>oracle-jdbc</artifactId>
		<version>11.2.0.4</version>
		<file>src/ojdbc6-11.2.0.4.jar</file>
		<url>file:///${basedir}/public</url>
	</configuration>
</plugin>
```

packaging ： 打包方式  <br/>
groupId：    发布包的groupId信息 <br/>
artifactId： 发布包的artifactId信息 <br/>
version：    发布包的版本信息 <br/>
file：       发布包的jar文件 <br/>
url：        可以在项目任意目录下 <br/>


然后，在项目根路径下执行deploy-file命令，即可完成发布jar包到本地路径
```
mvn deploy:deploy-file
```

## 2、提交代码到github上

## 3、在其他项目中，使用自己的maven私仓
自己私仓的地址，前面加一个raw前缀，即可，比如该私仓的地址为：
```xml
<repository>
	<id>maven-github</id>
	<url>https://raw.github.com/clever2020/maven-repo/master/public</url>
</repository>
```

本质上，就是提供的一个文件下载地址，自己可以加上具体完整依赖，看能不能下载。