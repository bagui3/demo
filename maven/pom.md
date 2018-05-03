打开pom.xml，最基础的是这样的：
<project xmlns="http://maven.apache.org/POM/4.0.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
     
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.xrq.withmaven</groupId>
  <artifactId>withmaven</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  <build/>
</project>

因为这个配置文件是Maven的核心，因此有必要详细解读一下pom.xml，来先看一下上面的几个：
1、modelVersion
    指定了当前Maven模型的版本号，对于Maven2和Maven3来说，它只能是4.0.0
2、groupId
    顾名思义，这个应该是公司名或是组织名。一般来说groupId是由三个部分组成，每个部分之间以"."分隔，第一部分是项目用途，比如用于商业的就是"com"，用于非营利性组织的就　　是"org"；第二部分是公司名，比如"tengxun"、"baidu"、"alibaba"；第三部分是你的项目名
3、artifactId
    可以认为是Maven构建的项目名，比如你的项目中有子项目，就可以使用"项目名-子项目名"的命名方式
4、version
    版本号，SNAPSHOT意为快照，说明该项目还在开发中，是不稳定的版本。在Maven中很重要的一点是，groupId、artifactId、version三个元素生成了一个Maven项目的基本坐标，这非常重要，我在使用和研究Maven的时候多次感受到了这点。