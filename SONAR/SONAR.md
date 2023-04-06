 1.
```
sudo amazon-linux-extras install epel -y

```
 2.
 ```
 sudo amazon-linux-extras install java-openjdk11 -y
 ```
 3.
 sudo -i\
 cd /opt
 4.
 ```
 yum install wget unzip -y
 ```
 5.
 ```
 wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-8.9.10.61524.zip
 ```
 6.
 ```
 unzip sonarqube-8.9.10.61524.zip
 ```
 7.
 ```
 useradd sonar
 ```
 8.
 visudo\
 9.
 ```
 sonar ALL=(ALL)     NOPASSWD:ALL
 ```
 10.
 ```
 chown -R sonar:sonar /opt/sonarqube-8.9.10.61524
 ```
 11.
 ```
 chmod -R 775 /opt/sonarqube-8.9.10.61524
 ```
 12.
 ```
 su - sonar
 ```
 13.
 ```
 cd /opt/sonarqube-8.9.10.61524/bin/linux-x86-64
 ```
 14.
 ```
 ./sonar.sh start
 ```
 15.
 ```
 ./sonar.sh status
 ```
 16.
 cd /opt\
 17.
 ```
 wget https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-4.2.0.1873-linux.zip
 ```
 18.
 ```
 unzip sonar-scanner-cli-4.2.0.1873-linux.zip
 ```
 19.
 ```
 mv sonar-scanner-4.2.0.1873-linux /opt/sonar-scanner
 ```
 20.
 ```
 vi /opt/sonar-scanner/conf/sonar-scanner.properties
 ```
 21.
 sonar.host.url=http://localhost:9000\
 sonar.sourceEncoding=UTF-8
 22.
 ```
 vi /etc/profile.d/sonar-scanner.sh
 ```
 23.
 ```
 #!/bin/bash
export PATH="$PATH:/opt/sonar-scanner/bin"
```
24.
```
source /etc/profile.d/sonar-scanner.sh
```
25.
env | grep PATH

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/opt/sonar-scanner/bin

26.
```
sonar-scanner -v
```
27.OUTPUT SHOULD BE \
INFO: Scanner configuration file: /opt/sonar-scanner/conf/sonar-scanner.properties\
INFO: Project root configuration file: NONE\
INFO: SonarQube Scanner 4.2.0.1873\
INFO: Java 11.0.3 AdoptOpenJDK (64-bit)\
INFO: Linux 5.3.0-18-generic amd64