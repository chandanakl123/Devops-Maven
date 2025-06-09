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
4. git remote add origin git repository 

5. git push -u origin master https://github.com/NANDITHA-nan/DevOps-GRD
6. mvn clean install
7. git add .
8.git commit -m "Deploy site to GitHub Pages"
9. git push -u origin master 
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


5.Jenkins

----commands 

1.wget https://get.jenkins.io/war/latest/jenkins.war
2.cd /home/ewit - ise/Downloads
3.java -jar jenkins.war
wget https://get.jenkins.io/war/latest/jenkins.war
cat

                                            or

1. wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add 
 sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ >
 /etc/apt/sources.list.d/jenkins.list'
2.sudo apt update
3.sudo apt install jenkins -y
4.sudo systemctl start jenkins
5.sudo systemctl enable jenkins
6.sudo cat /var/lib/jenkins/secrets/initialAdminPassword
7.http://localhost:8080

1.java -jar jenkins.war --httpPort=8080
2.http://localhost:8080



6.: Continuous Integration with Jenkins


cd copy and paste intellij terminal path
mvn test


7.Ansible

Open ubuntu
Type
>sudo apt upgrade
>sudo apt install ansible -y
>ansible --version
>mkdir ansible_project
>cd ansible_project
>nano host
It opens a tab there type
>[local]
>localhosts ansible_connection=local
Press ctrl+o then enter again ctrl+x
> ansible -i hosts local -m ping
> nano install_nginx.yml
It opens a tab there type-: 
---
- name: Install and start NGINX on localhost
  hosts: local
  become: yes

  tasks:
   - name: Install NGINX
     apt:
      name: nginx
      state: present
      update_cache: yes

   - name: Ensure NGINX is running
     service:
      name: nginx
      state: started
      enabled: yes
Press ctrl+o then enter again ctrl+x
> ansible-playbook -i hosts install_nginx.yml
> curl http://localhost


8.CI Pipeline

wsl -install
    suso apt install wsl
    sudo apt install wsl
    wsl
    sudo apt upgrade
    sudo apt install ansible -y
    ansible --version
    mkdir ansible_project
    mkdir ansible_project2
    cd ansible_project2
    nano host
    ansible -i host local -m ping
   nano install_nginx.yml
    ansible-playbook-i host install_nginx.yml
    ansible-playbook -i host install_nginx.yml
   nano host
    nano install_nginx.yml
   ansible-playbook -i host install_nginx.yml
    curl http://localhost
    ip addr

    ----Experiment 7: Configuration Management with Ansible 
Ansible Basics: 
1. Inventory: 
o Defines target hosts (INI or YAML format) 
o Groups hosts logically (web_servers, db_servers) 
o Can include host variables 
2. Playbooks: 
o YAML files defining automation tasks 
o Structure: 
▪ hosts: Target host group 
▪ become: Use sudo privileges 
▪ tasks: Actions to perform 
▪ handlers: Special triggered tasks 
3. Modules: 
o Reusable units of automation 
o Common modules: 
▪ apt/yum: Package management 
▪ copy: File transfer 
▪ service: Service management 
▪ file: File system operations 
Practical Example: Apache Setup 
1. Inventory (hosts.ini): 
[web_servers] 
server1.example.com 
server2.example.com 
2. Playbook (install_apache.yml): - name: Install and configure Apache 
hosts: web_servers 
become: yes 
tasks: - name: Install Apache 
apt: 
name: apache2 
state: present 
update_cache: yes - name: Start Apache service 
service: 
name: apache2 
state: started 
enabled: yes - name: Deploy index.html 
copy: 
content: "<html><h1>Welcome</h1></html>" 
dest: /var/www/html/index.html 
3. Execution: 
ansible-playbook -i hosts.ini install_apache.yml


Experiment 8: Jenkins CI with Ansible Deployment 
Integrated CI/CD Pipeline: 
1. Jenkins Setup: 
o Install required plugins (Maven, Ansible, Git) 
o Configure global tools (JDK, Maven, Ansible) 
o Set up credentials for target servers 
2. Pipeline Configuration: 
o Checkout code from Git repository 
o Build Maven project (clean install) 
o Archive generated artifact (JAR/WAR) 
o Trigger Ansible playbook for deployment 
3. Ansible Deployment Playbook: 
o Copy artifact from Jenkins workspace to target servers 
o Stop existing service 
o Deploy new artifact 
o Start service 
o Verify deployment 
Pipeline Example:  
pipeline { 
    agent any 
    tools { 
        maven 'Maven-3.8.6' 
    } 
    stages { 
        stage('Checkout') { 
            steps { 
                git 'https://github.com/your/repo.git' 
            } 
        } 
        stage('Build') { 
            steps { 
                sh 'mvn clean install' 
            } 
        } 
        stage('Deploy') { 
            steps { 
                ansiblePlaybook( 
                    playbook: 'deploy.yml', 
                    inventory: 'inventory.ini', 
                    credentialsId: 'ssh-key' 
                ) 
            } 
        } 
    } 
} 
Ansible Deployment Playbook (deploy.yml): - name: Deploy application 
  hosts: app_servers 
  become: yes 
  tasks: 
    - name: Copy artifact 
copy: 
src: "{{ workspace }}/target/myapp.jar" 
dest: "/opt/myapp/myapp.jar" - name: Restart service 
systemd: 
name: myapp 
state: restarted


 cd %WORKSPACE%
 mvn clean package

    











