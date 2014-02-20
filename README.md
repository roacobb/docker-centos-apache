# Prereq's 

This assumes that you have downloaded Vagrant (www.vagrantup.com), Oracle VM VirtualBox 
(www.virtualbox.org), and Docker (www.docker.io). 

# Starting your VM

  Create Vagrant Directory and switch to that directory  
```
  $mkdir ~/vagrant
  $cd ~/vagrant 
```

  Place the Vagrantfile here and create a htdocs directory parallel to that file
```
  $touch Vagrantfile #place code from this repo here
  $mkdir htdocs
```

  Switch to htdocs directory and create a index.html file
```
  $cd htdocs
  $touch index.html #place code from this repo here
```

  Switch back to ~/vagrant and vagrant up after that ssh into your VM
```
  $cd ..
  $vagrant up
  $vagrant ssh
```

  Install Docker
```
  $sudo yum -y update #Update installed packages
  $sudo yum -y install docker-io #Installing Docker
  $sudo service docker start #Starting Docker
```

# Building your Docker image and starting Apache

  Build your first Docker container image
```
  $sudo docker build -t -i myimage/base . #This will create an image called myimage/base 
                                           in the current directory
```

  Create a file called supervisord.conf in current directory  
```
  $touch supervisord.conf #Place contents of file in repo here
```

 Change contents of Dockerfile to reflect installing http server
```
  FROM myimage/base
  RUN yum -y install httpd
  ADD supervisord.conf /etc/supervisord.conf
  EXPOSE 22 80 
  CMD ["/usr/bin/supervisord"]
```

 Build another Docker image to reflect http server layer
```
 $sudo docker build -t -i myimage/httpd . #This creates an image called myimage/httpd
```

 Run the http server 
```
 $sudo docker run -p 80:80 -v /vagrant/htdocs:/var/www/html -t -i myimage/httpd
```

 Open a browser and test 

 Go to http://localhost:8080 in your browser

 
