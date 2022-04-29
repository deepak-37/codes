nexus  installation: path: /opt/nexus/bin/nexus(binary)
==============================================================================================================================================================
1. search-- download nexus on browser.
2.  you will find -----nexus repository and click on that.
3. downloads----download archives
    then launch instance -----pre-req: 
                                   4vcpu and 8gb needed.
                                   sg --22--vpn ip and 8081 ----myip 
4. connect to the ec2 by using command ssh ec2@publicip
5. cd /opt
6. get the nexus file from browser-----download nexus---downloads---unix archive---copy the link and paste it on the ec2.
7. like wget  https://download.sonatype.com/nexus/3/nexus-3.37.3-02-unix.tar.gz
8. tar -xvzf xxxxxxxxxxxx -----> to extract
9. ls -l
10. mv nexus--x.x.x.x.(version) to nexus --------->renaming.
11. cd /nexus
12. ls -l
13. cd /bin
14. useradd nexus
15. passwd nexus-----> retype password .
16. once the  password is updated 
17. visudo -----> add the nexus user to sudo.
----------------------------------------------------
nexus ALL=(ALL) NOPASSWD:ALL
------------------------------------------------
cd /opt
ls -l
chown -R nexus:nexus nexus
chown -R nexus:nexus sonatype-work
ls -l
cd/etc
sudo yum install java-1.8.0-openjdk-devel

vi /etc/systemd/system/nexus.service
------------------------------------------------------------------------------------
[Unit]
Description=nexus service
After=network.target
  
[Service]
Type=forking
LimitNOFILE=65536
ExecStart=/opt/nexus/bin/nexus start
ExecStop=/opt/nexus/bin/nexus stop
User=nexus
Restart=on-abort
TimeoutSec=600
  
[Install]
WantedBy=multi-user.target
----------------------------------------------------------------------------------------
:wq!
------------------------------------------------------------------------------------
systemctl enable nexus
systemctl restart nexus
systemctl status nexus
then copy the public ip of the nexus (ec2) and paste it on the browser publicip:8081
add username: admin
password : do not add password
To get password in a nexus page:  cat /opt/sonatype-work/nexus3/admin.password
* do not disable ananymous access.
================================================================================================================================================================
