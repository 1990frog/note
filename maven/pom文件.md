<!-- TOC -->

- [pom 节点](#pom-节点)
- [基本配置信息](#基本配置信息)
- [依赖配置](#依赖配置)
  - [parent](#parent)
  - [modules](#modules)
  - [properties](#properties)
  - [dependency 族](#dependency-族)
    - [scope 范围](#scope-范围)
    - [exclusions](#exclusions)
    - [dependencyMangement 与 dependencies 区别](#dependencymangement-与-dependencies-区别)
    - [dependencyMangement](#dependencymangement)
    - [dependencies](#dependencies)
- [构建配置](#构建配置)
- [环境设置](#环境设置)
  - [distributionManagement](#distributionmanagement)
  - [repositories](#repositories)

<!-- /TOC -->

# pom 节点
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
            http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <!-- 基本配置 -->
    <groupId>项目的组ID，用于maven定位</groupId>
    <artifactId>项目ID，通常是项目的名称,唯一标识符</artifactId>
    <version>项目的版本</version>
    <packaging>项目的打包方式</packaging>

    <!-- 依赖配置 -->
    <parent>用于确定父项目的坐标位置</parent>
    <dependencyManagement>在父模块中定义后，子模块不会直接使用对应依赖，但是在使用相同依赖的时候可以不加版本号</dependencyManagement>
    <dependencies>项目相关依赖配置</dependencies>
    <modules>多模块</modules>
    <properties>用于定义pom常量</properties>

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
packaging 区别：
+ pom：打出来的可以作为其他项目的maven依赖，在工程A中添加工程B的pom，A就可以使用B中的类。用在父级工程或聚合工程中。用来做jar包的版本控制。
+ jar：通常是开发时要引用通用类，达成jar包便于存放管理。当你使用某些功能时就需要这些jar包的支持，需要导入jar包。
+ war：是做好一个web网站后，打成war包部署到服务器。目的是节省资源，提供效率。

# 依赖配置
## parent
用于确定父项目的坐标位置
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
   <module>com-a</module>
   <module>com-b</module>
   <module>com-c</module>
<modules/>
```
## properties
用于定义pom常量
```xml
<properties>
    <java.version>1.7</java.version>
</properties>
```
## dependency 族
```xml
<dependency>
    <groupId>创建项目的组织或团体的唯一 Id.可视为公司名</groupId>
    <artifactId>项目的唯一 Id, 可视为项目名</artifactId>
    <version>产品的版本号</version>
    <scope>为jar包作用范围</scope>
    <exclusions></exclusions>
</dependency>
```
### scope 范围
默认的依赖范围是compile
1. test 范围指的是测试范围有效，在编译和打包时都不会使用这个依赖
2. compile 范围指的是编译范围有效，在编译和打包时都会将依赖存储进去
3. provided 依赖：在编译和测试的过程有效，最后生成war包时不会加入，诸如：servlet-api，因为servlet-api，tomcat等web服务器已经存在了，如果再打包会冲突
4. runtime 在运行的时候依赖，在编译的时候不依赖

### exclusions

### dependencyMangement 与 dependencies 区别
+ dependencies 即使在子项目中不写该依赖项，那么子项目仍然会从父项目中继承该依赖项（全部继承）
+ dependencyManagement 里只是声明依赖，并不实现引入，因此子项目需要显示的声明需要用的依赖。如果不在子项目中声明依赖，是不会从父项目中继承下来的；只有在子项目中写了该依赖项，并且没有指定具体版本，才会从父项目中继承该项，并且version和scope都读取自父pom;另外如果子项目中指定了版本号，那么会使用子项目中指定的jar版本。

### dependencyMangement
在父模块中定义后，子模块不会直接使用对应依赖，但是在使用相同依赖的时候可以不加版本号,这样的好处是，父项目统一了版本，而且子项目可以在需要的时候才引用对应的依赖。

在顶层pom中定义共同的依赖关系。同时可以避免在每个使用的子项目中都声明一个版本号，这样想升级或者切换到另一个版本时，只需要在父类容器里更新，不需要任何一个子项目的修改。

如果某个子项目需要另外一个版本号时，只需要在dependencies中声明一个版本号即可。子类就会使用子类声明的版本号，不继承于父类版本号。
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
### dependencies
相对于dependencyManagement，所有生命在dependencies里的依赖都会自动引入，并默认被所有的子项目继承。
```xml
<dependencies>
    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.12</version>
    </dependency>
</dependencies>
```
# 构建配置
```xml

```

# 环境设置
## distributionManagement

## repositories