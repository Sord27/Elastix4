# Elastix4onCentos7vz
###Install Elastix 4 on Centos 7 OpenVZ & Other VPS's

## Instalation
To start out, ssh into your host. Then at the command, download the install scripts. If you do not have wget, install it by `yum -y install wget`, then you will just need to run this:

	wget -O Elastix4onCentos7vz.tar.gz --no-check-certificate https://github.com/Sord27/Elastix4/archive/master.zip
	tar zxvf Elastix4onCentos7vz.tar.gz --strip-components=1 

If you are using the Digital Ocean 512 MB Memory / 20 GB Disk / NYC3 - CentOS 7.2 x64 setup, you will want to create a Swapfile, or else your memory will run out, and the database will crash. to do this, run `./create-swapfile.sh` 

If you are not installing on a VPS, and have hardware you want Elastix to support, then swap *inst2-hardware.txt* with *inst2.txt*

Then proceed to run the first install script:


	./elastix-install-p1.sh

This will download the Elastix Install DVD, unpack it to /mnt/iso, add it as a source to yum, then install all the files. It also adds Elastix's repo, so that it starts with the latest version. If you already have Elastix-4.0.74-Stable-x86_64-bin-10Feb2016.iso downloaded and in the same place as the install files, It will use it instead. Usefull if you find it on a faster Mirror.

Once it finishes, it needs to reboot. Reboot, then run the 2nd script

	./elastix-install-p2.sh
	
This will run the First-Run for Elastix that will have you setup the Mysql Database password, and your ADMIN password.

It will also clean off the install files so they won't take up space anymore.

After it finishes, it will have you reboot once more. Then you can configure through the Web interface, and however else you work with Elastix. 

If you can't access the web interface after the reboot, it is because you may have a firewall that is preventing it. To access it, you can temporarrly disable the firewall by running `systemctl stop iptables` and `systemctl stop firewalld`

###Be sure to configure the Firewall through Elastix, or however else you choose too.
