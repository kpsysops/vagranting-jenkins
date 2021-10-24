# vagranting-jenkins
[quickLabs] Setup jenkins in VMs on your local workstation with Vagrant 




## Windows prerequsits 

1. Install Vagrant (download from https://www.vagrantup.com/ & simple next,next,next)
2. Install Virutalbox (download from https://www.virtualbox.org/ & then next,next,next)

## Usage 

1. Download zip & unzip this GitHub repository

   or
```bash
git clone https://github.com/kpsysops/vagranting-jenkins.git
```

2. Change directory to directory downloaded (cloned) from this GitHub repository directory
3. Run:
```bash
vagrant up
```

4. Enjoy! 

## Notes

if you want to use java 8 (java-1-8-0) please do the following:
```
 sudo yum install java-1.8.0-openjdk.x86_64
 sudo sudo update-alternatives --config java
 sudo java -version
```

