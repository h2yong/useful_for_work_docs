# maven 配置

```xml
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
        <sourceEncoding>UTF-8</sourceEncoding>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <powermock.version>2.0.4</powermock.version>
        <spock.version>1.3-groovy-2.5</spock.version>
    </properties>

    <dependencies>
        <dependency>
            <groupId>org.powermock</groupId>
            <artifactId>powermock-module-junit4</artifactId>
            <version>${powermock.version}</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.powermock</groupId>
            <artifactId>powermock-api-mockito2</artifactId>
            <version>${powermock.version}</version>
            <scope>test</scope>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.assertj/assertj-core -->
        <dependency>
            <groupId>org.assertj</groupId>
            <artifactId>assertj-core</artifactId>
            <version>3.9.1</version>
            <scope>test</scope>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.hamcrest/hamcrest-all -->
        <dependency>
            <groupId>org.hamcrest</groupId>
            <artifactId>hamcrest-all</artifactId>
            <version>1.3</version>
            <scope>test</scope>
        </dependency>

        <!-- https://mvnrepository.com/artifact/com.jayway.jsonpath/json-path -->
        <dependency>
            <groupId>com.jayway.jsonpath</groupId>
            <artifactId>json-path</artifactId>
            <version>2.4.0</version>
            <scope>test</scope>
        </dependency>

        <dependency>
            <groupId>org.spockframework</groupId>
            <artifactId>spock-core</artifactId>
            <version>${spock.version}</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.spockframework</groupId>
            <artifactId>spock-spring</artifactId>
            <version>${spock.version}</version>
            <scope>test</scope>
        </dependency>
        <!-- test end -->

        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <version>1.18.6</version>
        </dependency>
    </dependencies>

    <build>
        <finalName>${project.artifactId}-${git.commit.id.abbrev}-${git.build.time}</finalName>
        <plugins>
            <plugin>
                <groupId>pl.project13.maven</groupId>
                <artifactId>git-commit-id-plugin</artifactId>
                <version>2.2.6</version>
                <executions>
                    <execution>
                        <goals>
                            <goal>revision</goal>
                        </goals>
                    </execution>
                </executions>
                <configuration>
                    <!-- 使properties扩展到整个maven bulid 周期
                    Ref: https://github.com/ktoso/maven-git-commit-id-plugin/issues/280 -->
                    <injectAllReactorProjects>true</injectAllReactorProjects>
                    <!--日期格式;默认值:dd.MM.yyyy '@' HH:mm:ss z;-->
                    <dateFormat>yyyyMMddHHmmss</dateFormat>
                    <!--,构建过程中,是否打印详细信息;默认值:false;-->
                    <verbose>true</verbose>
                    <!--是否生成"git.properties"文件;默认值:false;-->
                    <generateGitPropertiesFile>true</generateGitPropertiesFile>
                    <!-- ".git"文件路径;默认值:${project.basedir}/.git; ..表示上一级-->
                    <dotGitDirectory>${project.basedir}/../.git</dotGitDirectory>
                    <gitDescribe>
                        <!--提交操作ID显式字符长度,最大值为:40;默认值:7;0代表特殊意义;-->
                        <abbrev>7</abbrev>
                        <!--构建触发时,代码有修改时(即"dirty state"),添加指定后缀;默认值:"";-->
                        <dirty>-dirty</dirty>
                    </gitDescribe>
                </configuration>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                    <encoding>UTF-8</encoding>
                </configuration>
            </plugin>
            <!-- Mandatory plugins for using Spock -->
            <!-- 使用Spock的强制性插件 -->
            <plugin>
                <!-- The gmavenplus plugin is used to compile Groovy code. To learn more about this plugin,visit https://github.com/groovy/GMavenPlus/wiki -->
                <!-- 这个 gmavenplus 插件是用于编译Groovy代码的.想获取更多此插件相关信息,visit https://github.com/groovy/GMavenPlus/wiki -->
                <groupId>org.codehaus.gmavenplus</groupId>
                <artifactId>gmavenplus-plugin</artifactId>
                <version>1.8.1</version>
                <executions>
                    <execution>
                        <goals>
                            <goal>addSources</goal>
                            <goal>addTestSources</goal>
                            <goal>generateStubs</goal>
                            <goal>compile</goal>
                            <goal>generateTestStubs</goal>
                            <goal>compileTests</goal>
                            <goal>removeStubs</goal>
                            <goal>removeTestStubs</goal>
                        </goals>
                    </execution>
                </executions>
                <configuration>
                    <sources>
                        <source>
                            <directory>${project.basedir}/src/main/java</directory>
                            <includes>
                                <include>**/*.groovy</include>
                            </includes>
                        </source>
                    </sources>
                    <testSources>
                        <testSource>
                            <directory>${project.basedir}/src/test/java</directory>
                            <includes>
                                <include>**/*.groovy</include>
                            </includes>
                        </testSource>
                    </testSources>
                </configuration>
                <dependencies>
                    <dependency>
                        <groupId>org.codehaus.groovy</groupId>
                        <artifactId>groovy-all</artifactId>
                        <version>2.4.15</version>
                        <scope>runtime</scope>
                        <type>pom</type>
                    </dependency>
                </dependencies>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>2.22.2</version>
                <executions>
                    <execution>
                        <id>default-test</id>
                        <phase>test</phase>
                        <goals>
                            <goal>test</goal>
                        </goals>
                        <configuration>
                            <includes>
                                <include>**/*Test.java</include>
                                <include>**/*Spec.java</include>
                            </includes>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
            <plugin>
                <groupId>org.jacoco</groupId>
                <artifactId>jacoco-maven-plugin</artifactId>
                <version>0.8.5</version>
                <executions>
                    <execution>
                        <id>prepare-agent</id>
                        <goals>
                            <goal>prepare-agent</goal>
                        </goals>
                    </execution>
                    <execution>
                        <id>report</id>
                        <phase>prepare-package</phase>
                        <goals>
                            <goal>report</goal>
                        </goals>
                    </execution>
                    <execution>
                        <id>post-unit-test</id>
                        <phase>test</phase>
                        <goals>
                            <goal>report</goal>
                        </goals>
                        <configuration>
                            <dataFile>target/jacoco.exec</dataFile>
                            <outputDirectory>target/jacoco-ut</outputDirectory>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
```

# 测试用例

## 源文件 - Calculator.java

```java
public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
    public int substract(int a, int b) {
        return a - b;
    }
    public static String getVersion() {
        return "1.0";
    }
}
```

## 测试文件 - CalculatorTest.groovy

### 测试普通方法

```groovy
class CalculatorTest extends Specification {
    def "Add"() {
        given:
        def calculator = new Calculator()
        when:
        def result = calculator.add(1, 2)
        then:
        result == 3
        calculator.add(2, 3) == 5
    }

    def "Substract"() {
        given:
        def calculator = new Calculator()
        expect:
        result == calculator.substract(a, b)
        where:
        a | b || result
        5 | 3 || 2
        100 | 50 || 50
        1000 | 300 || 700
    }
}
```

### 测试静态方法

```groovy
@RunWith(PowerMockRunner)
@PowerMockRunnerDelegate(Sputnik)
@PrepareForTest([Calculator])
class CalculatorTest extends Specification {
    def "GetVersion"() {
    when:
    mockStatic(Calculator)
    doReturn("2.0").when(Calculator, "getVersion")
    then:
    Calculator.getVersion() == "2.0"
    }
}
```

# 整合会存在的问题

- <https://github.com/spockframework/spock/issues/1064>
