- Install Glassfish server and change HTTP port to 8088.
steps:   
      -sudo apt-get update
   install java
      -sudo add-apt-repository ppa:openjdk-r/ppa
      -sudo apt-get install openjdk-11-jre
   Set JAVA_HOME Path
      -sudo nana /etc/enviroment
      -export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
   checking version
      -java -version
      ![java version](https://user-images.githubusercontent.com/53372486/141651556-df9153bb-2138-4337-a658-822a027be2bd.png)
   
   install glassfish
      -https://github.com/eclipse-ee4j/glassfish/releases/download/6.2.2/glassfish-6.2.2.zip
      -unzip glassfish-4.1.zip -d /opt/
   start glassfish
      -cd /Downloads/glassfish-6.2.2/glassfish6/bin
      -./asadmin start-domain 
      ![glassfish start](https://user-images.githubusercontent.com/53372486/141651600-1b61f390-7bcf-4b77-93b5-8e06a065a821.png)
      ![glassfish admin](https://user-images.githubusercontent.com/53372486/141651610-55a0bab7-564e-4ab5-9c34-492903f8b484.png)

chnage http port to 8088
      -in admin console "Configuration" > "server-config" > "HTTP Service" > "Http Listeners" > "http-listener-1"
      -8080 change to  8088
         OR
      -cd /glassfish/domains/domain1/config
      -nano domain.xml
      find below line and change port 8080 to 8088
      -<network-listener port="8080" protocol="http-listener-1" transport="tcp" name="http-listener-1" thread-pool="http-thread-pool"></network-listener>
      ![http 8088](https://user-images.githubusercontent.com/53372486/141651631-e80d8a1d-f0bb-427b-8c7a-b030638e719e.png)
