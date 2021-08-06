## SpringBoot 加载外部JAR

### （一）spring-boot-maven-plugin 配置
```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
            <version>${spring_boot.version}</version>
            <configuration>
                <layout>ZIP</layout>
            </configuration>
            <executions>
                <execution>
                    <phase>package</phase>
                    <goals>
                        <goal>repackage</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>

```
`<configuration>`中增加`<layout>ZIP</layout>`配置，不配置该项也可以通过maven命令中增加`-Dspring-boot.repackage.layout=ZIP`

### （二）maven 打包
```shell
	mvn clean package 

```
或者
```shell
	mvn clean package -Dspring-boot.repackage.layout=ZIP

```

### (三)运行jar
```shell
	java -Dloader.path=XXX -jar yourjar.jar

```