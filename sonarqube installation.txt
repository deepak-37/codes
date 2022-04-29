Sonarqube installation:
=============================
Pre -requisites:
Ec2 machine with minimum requirement of 2 GB RAM (t2.small)
Java 11 version is needed.

Process:
Create ec2 machine with 2GB of ram machine.
Sonarqube runs on port number 9000.
In security group allow 9000 - anywhere and 22 - vpn ip
Sonarqube won’t run with root user.
connect to the ec2 after connecting to it. 
Create a user by using command  useradd <name> Ex: useradd sonaradmin
Check the user by using command id sonaradmin in this case.
Then, go to sonaqrube website by using the following link Download | SonarQube
There at the longterm support section, in the right side we can find community edition option.
Right click on that and copy the link.
Then go to opt folder in the ec2 machine.
Use wget <link> to download sonarqube and unzip it by using command unzip <the file sonarqube>
Then, change the ownership to new user, in this case to sonaradmin.
Use command chown -R sonaradmin:sonaradmin <sonarqube file name>
Change user to sonaradmin and go to the /opt path
In the list of that folder we can find bin folder.
In bin we can see different os types as we are going for linux select linux os in that list.
Go to that path and in that we can find the file called sonar.sh
Use ./sonar.sh to list the commands
Start sonarqube by using ./sonar.sh start
See status by using ./sonar.sh startus
Finally take the public ip of that ec2 and paste in browser followed by :9000 port number.
Default user name is admin and the default password is admin
In the next page we can change the user and password.


===================================================
===================================================
SonarQube Install:
==================
https://github.com/ravdy

Require Java 11
Min 4 vCPU & 4 GB Memory ---> t2.small
Port 9000 opened
    8  yum list | grep openjdk
    9  amazon-linux-extras list
   10  amazon-linux-extras install java-openjdk11
   11  java -version
   12  cd /opt
   13  ll
   14  wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-8.9.7.52159.zip
   15  ll
   16  unzip sonarqube-8.9.7.52159.zip
   17  ll
   18  adduser sonaradmin
   19  id sonaradmin
   20  chown -R sonaradmin:sonaradmin sonarqube-8.9.7.52159
   21  ll
   22  cd sonarqube-8.9.7.52159/
   23  ll
   24  cd bin
   25  ll
   26  cd linux-x86-64/
   27  ll
   28  chmod -R 777 /opt/sonarqube-8.9.7.52159/
   29  su - sonaradmin
   30   cd /opt/
   31  cd /sonarqube-8.9.7.52159/bin/linux-x86-64/
   32  ll
   33  cd sonarqube-8.9.7.52159/
   34  ll
   36  cd bin
   37  ll
   38  cd linux-x86-64/
   39  ll
   40  ./sonar.sh start
   41  ./sonar.sh status
   42  ll

then access the webpage by using public Ip
default credentials:
username: admin
passwd  : admin
===============================
if you stop and start the instance you need to do start the service by using following commands:
  29  su - sonaradmin
   30   cd /opt/
   31   cd sonarqube-8.9.7.52159/
   34  ll
   36  cd bin
   37  ll
   38  cd linux-x86-64/
   39  ll
   40  ./sonar.sh start
   41  ./sonar.sh status
   







