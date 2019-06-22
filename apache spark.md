instalacion de java:

sudo apt update
sudo apt install dirmngr

 sh -c 'echo "deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" >>
 /etc/apt/sources.list' &&  sh -c 'echo "deb-src
 http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" >>
/etc/apt/sources.list' &&  apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 
--recv-keys EEA14886

sudo apt update
sudo apt install oracle-java8-installer -y
java -version
--------------------------------------------------------------------------------------------------
instalacion de scala:
	 wget https://downloads.lightbend.com/scala/2.13.0-M1/scala-2.13.0-M1.deb
	 dpkg -i scala-2.13.0-M1.deb

	scala -version
	scala
------------------------------------------------------------------------------------------------
instalacion y configuracion de openssh
	apt-get install openssh-server

	 nano /etc/ssh/sshd_config
		editar PermitRootLogin yes
-------------------------------------------------------------------------------------------------
instalacion apachespark:
	wget http://d3kbcqa49mib13.cloudfront.net/spark-2.1.0-bin-hadoop2.7.tgz
	mkdir /opt/spark
	tar -xzvf spark-2.1.0-bin-hadoop2.7.tgz
	mv spark-2.1.0-bin-hadoop2.7/* /opt/spark/

	nano ~/.bashrc
	export SPARK_HOME=/opt/spark/
	export PATH="/opt/spark/bin/:/opt/spark/sbin/:$PATH"

	source ~/.bashrc

--------------------------------------------------------------------------------------------------
configuracion openssh(todo esto en el spark master)
	ssh-keygen
	ssh-copy-id -i ~/.ssh/id_rsa.pub root@ip_de_la_maquina

-------------------------------------------------------------------------------------------------
Configuración de Apache Spark en el servidor master
	cp slaves.template slaves
	nano slaves(añadir direccion del worker):
	# A Spark Worker will be started on each of the machines listed below.
	# localhost
	192.168.3.2

	cp spark-env.sh.template spark-env.sh
	nano spark-env.sh
	export SPARK_MASTER_HOST=192.168.2.2 # En mi caso: 192.168.2.2
	export SPARK_WORKER_CORES=1 # Número de cores que se ejecutan en el servidor.
	export SPARK_WORKER_INSTANCES=1 # Número de procesos worker por cada nodo.	

	
