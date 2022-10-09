Automation bash script

Prerequsites
--> Install AWS cli
--> Intsall git 

Task 2
Running ./automation.sh with root privileges must do the following listed tasks.
    Perform an update of the package details and the package list at the start of the script.
     
    Install the apache2 package if it is not already installed. (The dpkg and apt commands are used to check the installation of the packages.)
   
    Ensure that the apache2 service is running. 
   
    Ensure that the apache2 service is enabled. (The systemctl or service commands are used to check if the services are enabled and running. Enabling apache2 as a service ensures that it runs as soon as our machine reboots. It is a daemon process that runs in the background.)
   
    Create a tar archive of apache2 access logs and error logs that are present in the /var/log/apache2/ directory and place the tar into the /tmp/ directory. Create a tar of only the .log files (for example access.log) and not any other file type (For example: .zip and .tar) that are already present in the /var/log/apache2/ directory. The name of tar archive should have following format:  <your _name>-httpd-logs-<timestamp>.tar. For example: Ritik-httpd-logs-01212021-101010.tar                                                             Hint : use timestamp=$(date '+%d%m%Y-%H%M%S') )
    The script should run the AWS CLI command and copy the archive to the s3 bucket.

Task 3

There are two significant areas of improvement in our previous script.
 
No bookkeeping of archived files 
Currently, there is no record of compressed logs file getting copied to s3 via AWS CLI. We don't have a history of how many compressed tar files are copied to s3, their names, and the time when the copy process ended.
 
Manual execution of the script
Presently, the script has to be manually executed by an engineer every time. It should, however, be automatically run at a regular interval of time by a cron job.
 
In this task you will essentially upgrade the existing automation.sh script such that script will create a record when the tar file is copied from the EC2 to s3. Also, the script itself will set a cron job that will run the script at a regular interval of time.
