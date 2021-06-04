[TOC]

# 将本地包添加至仓库
```
> mvn install:install-file -Dfile=path/xxx.jar -DgroupId=com.aspose -DartifactId=DartifactId -Dversion=Dversion -Dpackaging=jar -Dclassifier=Dclassifier
```

# 创建Maven的普通Java项目
```
> mvn archetype:create
    -DgroupId=packageName
    -DartifactId=projectName
```

# 创建Maven的Web项目
```

> mvn archetype:create
    -DgroupId=packageName
    -DartifactId=webappName
    -DarchetypeArtifactId=maven-archetype-webapp
```

# 编译源代码
```
> mvn compile
```

# 编译测试代码
```
> mvn test-compile
```

# 运行ces
```
> mvn test
```

# 打包
```
> mvn package
```

# 本地仓库装包
```
> mvn install
```

# 清除产生的项目
```
> mvn clean
```

# 生成idea项目
```
> mvn idea:idea
```

# 组合使用goal命令，如只打包不测试
```
> mvn -Dtest package
```

# 只打jar包
```
> mvn jar:jar
```

# 清除eclipse的一些系统设置
```
> mvn eclipse:clean
```

# 查看当前项目已被解析的依赖
```
> mvn dependency:list
```

# 上传到私服
```
> mvn deploy
```

# 强制检查更新，由于快照版本的更新策略(一天更新几次、隔段时间更新一次)存在，如果想强制更新就会用到此命令
```
> mvn clean install-U
```

# 源码打包
```
> mvn source:jar
```

# mvn compile与mvn install、mvn deploy的区别
+ mvn compile，编译类文件
+ mvn install，包含mvn compile，mvn package，然后上传到本地仓库
+ mvn deploy,包含mvn install,然后，上传到私服

# 打包并跳过检查
mvn package -Dmaven.test.skip=true
