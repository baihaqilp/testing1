// Powered by Infostretch 

timestamps {

node () {

	stage ('job2 - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/dev']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github_id', url: 'https://github.com/baihaqilp/testing1.git']]]) 
	}
	stage ('job2 - Build') {
 			// Shell build step
sh """ 
sudo cp -v -r -f /var/www/web_deploy/test1 /lwweb

if sudo docker ps | grep mywebos
then
echo "already running"
else
sudo docker run -d -t -i -p 8085:80 -v /lwweb:/usr/local/apache2/htdocs --name mywebos httpd
fi 
 """ 
	}
	stage ('job1 - Build') {
 			// Shell build step
sh """ 
sudo cp -v -r -f /var/www/web_deploy/test1 /lwweb
if sudo docker ps | grep prodos
then
echo "already running"
else
sudo docker run -d -t -i -p 8082:80 -v /lwweb:/usr/local/apache2/htdocs --name prodos httpd
fi 
 """ 
	}
}
}