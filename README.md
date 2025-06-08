2.MAVEN

----Maven pom.xml

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>DevOpsVTU-Maven</artifactId>
    <version>1.0-SNAPSHOT</version>
    <dependencies>
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>4.28.1</version>
        </dependency>
        <dependency>
            <groupId>org.testng</groupId>
            <artifactId>testng</artifactId>
            <version>7.4.0</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-resources-plugin</artifactId>
                <version>3.2.0</version>
                <executions>
                    <execution>
                        <phase>prepare-package</phase> <!-- Before packaging -->
                        <goals>
                            <goal>copy-resources</goal>
                        </goals>
                        <configuration>
                            <outputDirectory>${project.basedir}/docs</outputDirectory> <!-- Deploy to /docs -->
                            <resources>
                                <resource>
                                    <directory>src/main/resources</directory> <!-- Source directory -->
                                    <includes>
                                        <include>*/</include> <!-- Copy all files in src/main/resources -->
                                    </includes>
                                </resource>
                            </resources>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>

    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

</project>


---Css for Maven

body {
 font-family: Arial, sans-serif;
 background-color: #f4f4f4;
 text-align: center;
}
header img {
 width: 100px;
}


----HTML for Maven

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>My Simple Website</title>
<link rel="stylesheet" href="mvn.css">
</head>
<body>
<header>
<img src="welcome1.png" alt="Logo">
</header>
<h1>Welcome to My Simple Website</h1>
</body>
</html>

----Webpage test for Maven:org.test

package org.test;

import org.openqa.selenium.WebDriver;
  import org.openqa.selenium.chrome.ChromeDriver;
  import org.testng.Assert;
  import org.testng.annotations.AfterTest;
  import org.testng.annotations.BeforeTest;
 import org.testng.annotations.Test;
 
  import static org.testng.Assert.assertTrue;
 
  public class WebpageTest {
     private static WebDriver driver;
 
     @BeforeTest
     public void openBrowser() throws InterruptedException {
         driver = new ChromeDriver();
         driver.manage().window().maximize();
         Thread.sleep(2000);
         driver.get("https://github.com/NANDITHA-nan/DevOps-MVN"); // "Note: You should use your GITHUB-URL here...!!!"
     }
 
     @Test
     public void titleValidationTest(){
        String actualTitle = driver.getTitle();
        String expectedTitle = "My Simple Website";// title should be match with the index.html title
         Assert.assertEquals(driver.getTitle(), "GitHub - NANDITHA-nan/DevOps-MVN: maven");
         //given github login  username and the repository name with description 

         assertTrue(true, "Title should contain 'ci/cd'");
    }
 
     @AfterTest
     public void closeBrowser() throws InterruptedException {
         Thread.sleep(1000);
         driver.quit();
    }
  }


----Commands

1.git init
2. git add .
3. git commit -m "Initial commit"
4. git remote add origin
5. git push -u origin master https://github.com/NANDITHA-nan/DevOps-GRD
6. mvn clean install
7. git add docs/*
8.git commit -m "Deploy site to GitHub Pages"
9. git push origin master 
10. https://.github.io//


3. GRADLE

   ----Build.gradle for gradle

plugins {
    id 'application'
}
 repositories {
    mavenCentral()
}
 dependencies {
     // https://mvnrepository.com/artifact/org.seleniumhq.selenium/selenium-java
     // https://mvnrepository.com/artifact/org.seleniumhq.selenium/selenium-java
     implementation group: 'org.seleniumhq.selenium', name: 'selenium-java', version: '4.33.0' //gradle long
     // https://mvnrepository.com/artifact/org.testng/testng
     testImplementation group: 'org.testng', name: 'testng', version: '7.11.0'
}
 application {
     mainClass = 'org.example.Main'
}


----Css for Gradle

body {
 font-family: Arial, sans-serif;
 background-color: #f4f4f4;
 text-align: center;
}
header img {
 width: 100px;
}


----HTML for Gradle

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>My Simple Website</title>
<link rel="stylesheet" href="mvn.css">
</head>
<body>
<header>
<img src="welcome1.png" alt="Logo">
</header>
<h1>Welcome to My Simple Website</h1>
</body>
</html>


----Webpage test for gradle

package org.test;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.Assert;
import org.testng.annotations.AfterTest;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.Test;

import static org.testng.Assert.assertTrue;

public class WebpageTest {
    private static WebDriver driver;

    @BeforeTest
    public void openBrowser() throws InterruptedException {
        driver = new ChromeDriver();
        driver.manage().window().maximize();
        Thread.sleep(2000);
        driver.get("https://github.com/NANDITHA-nan/DevOps-GRD"); // "Note: You should use your GITHUB-URL here...!!!"
    }

    @Test
    public void titleValidationTest(){
        String actualTitle = driver.getTitle();
        String expectedTitle = "My Simple Website";// title should be match with the index.html title
        Assert.assertEquals(driver.getTitle(), "GitHub - NANDITHA-nan/DevOps-GRD");
        //given github login  username and the repository name with description

        assertTrue(true, "Title should contain 'ci/cd'");
    }

    @AfterTest
    public void closeBrowser() throws InterruptedException {
        Thread.sleep(1000);
        driver.quit();
    }
}


----Commands

1.git init
2. git add .
3. git commit -m "Initial commit"
4. git remote add origin
5. git push -u origin master https://github.com/NANDITHA-nan/DevOps-GRD
6. mvn clean install
7. git add docs/*
8.git commit -m "Deploy site to GitHub Pages"
9. git push origin master 
10. https://.github.io//
11.gradle test
12.gradle jar
13.java -jar ./build/libs/DevOpsVTU-Gradle.jar

4.MIGRATION

----Maven pom.xml

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>DevOps-VTU-MVN-To-GRD</artifactId>
    <version>1.0-SNAPSHOT</version>

    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>1.8</source>  <!-- Java version -->
                    <target>1.8</target>
                </configuration>
            </plugin>

            <!-- JAR Plugin -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-jar-plugin</artifactId>
                <version>3.2.0</version>
                <configuration>
                    <archive>
                        <manifest>
                            <addClasspath>true</addClasspath>
                            <mainClass>org.example.Main</mainClass> <!-- Replace with your main class -->
                        </manifest>
                    </archive>
                </configuration>
            </plugin>
        </plugins>
    </build>

</project>

----Gradle build.gradle


/*
 * This file was generated by the Gradle 'init' task.
 *
 * This project uses @Incubating APIs which are subject to change.
 */

plugins {
    id 'java-library'
    id 'maven-publish'
    id 'java'
}

repositories {
    mavenLocal()
    maven {
        url = uri('https://repo.maven.apache.org/maven2/')
    }
}

group = 'org.example'
version = '1.0-SNAPSHOT'
description = 'DevOps-VTU-MVN-To-GRD'
java.sourceCompatibility = JavaVersion.VERSION_1_8

publishing {
    publications {
        maven(MavenPublication) {
            from(components.java)
        }
    }
}

tasks.withType(JavaCompile) {
    options.encoding = 'UTF-8'
}

tasks.withType(Javadoc) {
    options.encoding = 'UTF-8'
}
dependencies {
    testImplementation 'junit:junit:4.13.2'
}
jar {
    manifest{
        attributes(
                'Main-Class':'org.example.Main'
        )
    }
}

----Commands

1.mvn clean compile
2.mvn package
3.java -jar ./target/DevOps-VTU-MVN-To-GRD-1.0-SNAPSHOT.jar
4.mvn clean install
5.gradle init --type pom
6.gradle clean build
7.java -jar ./build/libs/DevOps-VTU-MVN-To-GRD-1.0-SNAPSHOT.jar











