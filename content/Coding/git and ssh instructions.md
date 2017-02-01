Command line instructions

Git global setup

	git config --global user.name "Ned Yoxall"
	git config --global user.email "edward.yoxall1@royalmail.com"

Create a new repository

	git clone git@rmgrhhdilin101.rmgp.royalmailgroup.net:yoxalln/RouteGPS.git
	cd RouteGPS
	touch README.md
	git add README.md
	git commit -m "add README"
	git push -u origin master

Existing folder or Git repository

	cd existing_folder
	git init
	git remote add origin git@rmgrhhdilin101.rmgp.royalmailgroup.net:yoxalln/RouteGPS.git
	git add .
	git commit
	git push -u origin master


SSH JAZZ:

An SSH key allows you to establish a secure connection between your computer and GitLab.

Before generating an SSH key, check if your system already has one by running `cat ~/.ssh/id_rsa.pub`. If you see a long string starting with ssh-rsa or ssh-dsa, you can skip the ssh-keygen step.

To generate a new SSH key, just open your terminal and use code below. The ssh-keygen command prompts you for a location and filename to store the key pair and for a password. When prompted for the location and filename, you can press enter to use the default.

It is a best practice to use a password for an SSH key, but it is not required and you can skip creating a password by pressing enter. Note that the password you choose here can't be altered or retrieved.

	ssh-keygen -t rsa -C "edward.yoxall1@royalmail.com"
Use the code below to show your public key.

	cat ~/.ssh/id_rsa.pub