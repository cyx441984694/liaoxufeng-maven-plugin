# Testing： To deploy artifcat to local

### Step1: Add the following in the POM.xml

	<distributionManagement>
		<repository>
			<id>local-repo-release</id>
			<name>Github Release</name>
			<url>file://${project.basedir}/maven-repo</url>
		</repository>
	</distributionManagement>
  
//Add source code and javadoc if required.

```
  <plugin>
				<artifactId>maven-source-plugin</artifactId>
				<executions>
					<execution>
						<id>attach-sources</id>
						<phase>package</phase>
						<goals>
							<goal>jar-no-fork</goal>
						</goals>
					</execution>
				</executions>
			</plugin>
			<plugin>
				<artifactId>maven-javadoc-plugin</artifactId>
				<executions>
					<execution>
						<id>attach-javadoc</id>
						<phase>package</phase>
						<goals>
							<goal>jar</goal>
						</goals>
					</execution>
				</executions>
			</plugin>
```
### Step2: push to github

### Step3: Settings>> Github Pages>>> source to main.

##  When you want to use that artifact
### Step1: Add <repository> and <dependency> to POM
Create a project like "how-to-get-artifact-usage". In POM:
```
   <repositories>
        <repository>
            <id>github-plugin-repo</id>
            <name>The maven repository on Github</name>
            <url>https://cyx441984694.github.io/liaoxufeng-maven-plugin/maven-repo/</url>
        </repository>
    </repositories>
    <dependencies>
        <dependency>
            <groupId>com.itranswarp.learnjava</groupId>
            <artifactId>hello-plugin</artifactId>
            <version>1.0-SNAPSHOT</version>
        </dependency>
    </dependencies>
```

### Step2:
Call the method in your main class, e.g:
```
import com.itranswarp.learnjava.Main;
        Main mai = new Main();
        System.out.println(mai.toString());
```
