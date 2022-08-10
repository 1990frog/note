
<!-- TOC -->

- [pom 节点](#pom-节点)
- [基本配置信息](#基本配置信息)
- [依赖配置](#依赖配置)
  - [dependencies](#dependencies)
  - [parent](#parent)
  - [modules](#modules)
  - [properties](#properties)
  - [dependencyManagement](#dependencymanagement)
- [构建配置](#构建配置)

<!-- /TOC -->
# pom 节点
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
            http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <!-- 基本配置 -->
    <groupId>...</groupId>
    <artifactId>...</artifactId>
    <version>...</version>
    <packaging>...</packaging>

    <!-- 依赖配置 -->
    <dependencies>...</dependencies>
    <parent>...</parent>
    <dependencyManagement>...</dependencyManagement>
    <modules>...</modules>
    <properties>...</properties>

    <!-- 构建配置 -->
    <build>...</build>
    <reporting>...</reporting>

    <!-- 项目信息 -->
    <name>...</name>
    <description>...</description>
    <url>...</url>
    <inceptionYear>...</inceptionYear>
    <licenses>...</licenses>
    <organization>...</organization>
    <developers>...</developers>
    <contributors>...</contributors>

    <!-- 环境设置 -->
    <issueManagement>...</issueManagement>
    <ciManagement>...</ciManagement>
    <mailingLists>...</mailingLists>
    <scm>...</scm>
    <prerequisites>...</prerequisites>
    <repositories>...</repositories>
    <pluginRepositories>...</pluginRepositories>
    <distributionManagement>...</distributionManagement>
    <profiles>...</profiles>
</project>
```

# 基本配置信息
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
   http://maven.apache.org/xsd/maven-4.0.0.xsd">
   <!-- pom模型版本，maven2和3只能为4.0.0-->
   <modelVersion>4.0.0</modelVersion>
   <!-- 项目的组ID，用于maven定位-->
   <groupId>com.company.bank</groupId>
   <!-- 项目ID，通常是项目的名称,唯一标识符-->
   <artifactId>parent</artifactId>
   <!-- 项目的版本-->
   <version>1.0</version>
   <!-- 项目的打包方式-->
   <packaging>pom,jar,maven-plugin,ejb,war,ear,rar,par</packaging>
<project>
```

# 依赖配置
## dependencies
项目相关依赖配置，如果在父项目写的依赖，会被子项目引用。一般会在父项目中定义子项目中所有共用的依赖。
```xml
<dependencies>
    <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
    </dependency>
</dependencies>
```
## parent
用于确定父项目的坐标位置。
```xml
<parent>
    <!-- 父项目的组Id标识符 -->
    <groupId>com.learnPro</groupId>
    <!-- 父项目的唯一标识符 -->
    <artifactId>SIP-parent</artifactId>
    <!-- Maven首先在当前项目中找父项目的pom，然后在文件系统的这个位置（relativePath），然后在本地仓库，再在远程仓库找 -->
    <relativePath></relativePath>
    <!-- 父项目的版本 -->
    <version>0.0.1-SNAPSHOT</version>
</parent>
```
## modules
有些maven项目会做成多模块的，这个标签用于指定当前项目所包含的所有模块。之后对这个项目进行的maven操作，会让所有子模块也进行相同操作。
```xml
<modules>
   <module>com-a</>
   <module>com-b</>
   <module>com-c</>
<modules/>
```
## properties
用于定义pom常量
```xml
<properties>
    <java.version>1.7</java.version>
</properties>
```
## dependencyManagement
在父模块中定义后，子模块不会直接使用对应依赖，但是在使用相同依赖的时候可以不加版本号,这样的好处是，父项目统一了版本，而且子项目可以在需要的时候才引用对应的依赖。
```xml
<!-- 父项目 -->
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
</dependencyManagement>
<!-- 子项目 -->
<dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
</dependency>
```

# 构建配置
```xml

```