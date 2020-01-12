# Maven

*  [官方预览](http://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)
*  [官方教程](http://maven.apache.org/guides/getting-started/index.html)

## hello world

### 生成空项目

```bash
# 生成空项目
mvn archetype:generate
```

接下来按照提示选择第 7 个，即输入 7。

```
[INFO] Scanning for projects...
[INFO]
[INFO] --------------------------< cn.quaeast:demo >---------------------------
[INFO] Building demo 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] >>> maven-archetype-plugin:3.1.2:generate (default-cli) > generate-sources @ demo >>>
[INFO]
[INFO] <<< maven-archetype-plugin:3.1.2:generate (default-cli) < generate-sources @ demo <<<
[INFO]
[INFO]
[INFO] --- maven-archetype-plugin:3.1.2:generate (default-cli) @ demo ---
[INFO] Generating project in Interactive mode
[WARNING] No archetype found in remote catalog. Defaulting to internal catalog
[INFO] No archetype defined. Using maven-archetype-quickstart (org.apache.maven.archetypes:maven-archetype-quickstart:1.0)
Choose archetype:
1: internal -> org.apache.maven.archetypes:maven-archetype-archetype (An archetype which contains a sample archetype.)
2: internal -> org.apache.maven.archetypes:maven-archetype-j2ee-simple (An archetype which contains a simplifed sample J2EE application.)
3: internal -> org.apache.maven.archetypes:maven-archetype-plugin (An archetype which contains a sample Maven plugin.)
4: internal -> org.apache.maven.archetypes:maven-archetype-plugin-site (An archetype which contains a sample Maven plugin site.
      This archetype can be layered upon an existing Maven plugin project.)
5: internal -> org.apache.maven.archetypes:maven-archetype-portlet (An archetype which contains a sample JSR-268 Portlet.)
6: internal -> org.apache.maven.archetypes:maven-archetype-profiles ()
7: internal -> org.apache.maven.archetypes:maven-archetype-quickstart (An archetype which contains a sample Maven project.)
8: internal -> org.apache.maven.archetypes:maven-archetype-site (An archetype which contains a sample Maven site which demonstrates
      some of the supported document types like APT, XDoc, and FML and demonstrates how
      to i18n your site. This archetype can be layered upon an existing Maven project.)
9: internal -> org.apache.maven.archetypes:maven-archetype-site-simple (An archetype which contains a sample Maven site.)
10: internal -> org.apache.maven.archetypes:maven-archetype-webapp (An archetype which contains a sample Maven Webapp project.)
Choose a number or apply filter (format: [groupId:]artifactId, case sensitive contains): 7:
```

根据提示设置项目属性，最后输入 `y` 确认。

```
Choose a number or apply filter (format: [groupId:]artifactId, case sensitive contains): 7: 7
Define value for property 'groupId': cn.quaeast
Define value for property 'artifactId': helloDemo
Define value for property 'version' 1.0-SNAPSHOT: :
Define value for property 'package' cn.quaeast: :
Confirm properties configuration:
groupId: cn.quaeast
artifactId: helloDemo
version: 1.0-SNAPSHOT
package: cn.quaeast
 Y: :
```

输入 `y`之后，mvn开始构建，输出构建成功的结果如下

```
 Y: : y
[INFO] ----------------------------------------------------------------------------
[INFO] Using following parameters for creating project from Old (1.x) Archetype: maven-archetype-quickstart:1.1
[INFO] ----------------------------------------------------------------------------
[INFO] Parameter: basedir, Value: /Users/fang/Desktop/github_repos/mvnTest
[INFO] Parameter: package, Value: cn.quaeast
[INFO] Parameter: groupId, Value: cn.quaeast
[INFO] Parameter: artifactId, Value: helloDemo
[INFO] Parameter: packageName, Value: cn.quaeast
[INFO] Parameter: version, Value: 1.0-SNAPSHOT
[INFO] project created from Old (1.x) Archetype in dir: /Users/fang/Desktop/github_repos/mvnTest/helloDemo
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  21.421 s
[INFO] Finished at: 2020-01-13T00:11:41+08:00
[INFO] ------------------------------------------------------------------------
```

### 构建

设置 java 版本，在 pom.xml 中加入：

```xml
  <properties>
    <maven.compiler.source>11</maven.compiler.source>
    <maven.compiler.target>11</maven.compiler.target>
  </properties>
```

运行命令

```bash
mvn compile
```

编译成功的输出结果

```
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------< cn.quaeast:helloDemo >------------------------
[INFO] Building helloDemo 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ helloDemo ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /Users/fang/Desktop/github_repos/mvnTest/helloDemo/src/main/resources
[INFO]
[INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ helloDemo ---
[INFO] Nothing to compile - all classes are up to date
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.555 s
[INFO] Finished at: 2020-01-13T00:17:03+08:00
[INFO] ------------------------------------------------------------------------
```

运行程序

```bash
mvn exec:java -Dexec.mainClass="cn.quaeast.App"
```

输出正确结果：Hello World!

```
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------< cn.quaeast:helloDemo >------------------------
[INFO] Building helloDemo 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- exec-maven-plugin:1.6.0:java (default-cli) @ helloDemo ---
Hello World!
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.532 s
[INFO] Finished at: 2020-01-13T00:17:47+08:00
[INFO] ------------------------------------------------------------------------
```

## 使用lombok

在 pom.xml 中添加依赖：

```xml
<dependencies>
    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
        <version>1.18.10</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```

测试

```bash
mvn test
```

