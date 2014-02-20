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

  Build your first Docker container image
```
  $sudo docker build -t -i myimage/base . #This will create an image called myimage/base 
                                           in the current directory
```



 
