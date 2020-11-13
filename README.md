# Infrastructure as a Code using AWS Cloudformation
The purpose of this project is to launch a static website from a S3 bucket using cloudformation.


# INFRASTRUCTURE DIAGRAM
![image](img/s3_website_deployment.png)


# HOW TO USE FILES IN REPO

create.sh
---------------

Run `bash create.sh stackname  file.yaml file.json`

Replace `stackname` with the a name for your stack
Replace `file.yaml` with your infrastructure resources yaml file
Replace `file.json` with your infrastructure parameter file

delete.sh
----------------
Run `bash delete.sh stackname`

Replace `stackname` with the a name for your stack

environment.json
-----------------------
Contains the json parameter file for your network environments. Can be used to change the environment name


environment.yaml
-----------------------
Contains the yaml file to launch the network environment resources


s3servers.json
---------------------
Contains the json parameter file for your servers. Can be used the change the environment name for your Servers


s3servers.yaml
--------------------
Contains the yaml file to launch the servers to host your apps


update.sh
-------------------
Run `bash update.sh stackname  file.yaml file.json`

Replace `stackname` with the a name for your stack
Replace `file.yaml` with your infrastructure resources yaml file
Replace `file.json` with your infrastructure parameter file


website.zip
-------------------
Contains a zipped website code


# STEP BY STEP GUIDE TO LAUNCH WEBSITE ON AWS
* Run `git clone repo`

* Run `cd repo`

* Run `bash create.sh s3environments environment.yaml environment.json`

* Wait for s3environments stack to be created

* Run `bash create.sh s3servers s3servers.yaml s3servers.json`

* Wait for s3servers stack to be created

* Click on the loadbalancer output URL in the s3 server stack to view website.
  This step may take a few minutes to configure
  ![image](img/loadbalancer_URL.png)

* Run `bash delete.sh s3environments`

* Wait for s3environments stack to be deleted

* Run `bash delete.sh s3servers`

* Verify stack is deleted in console to avoid recurring charges


Loadbalancer output should look like this
-----------------------------------------------
![image](img/website_screenshot.png)
