# AWS_EC2_instance
Documentation for creating an EC2 instance with AWS, connecting to AMI with PuTTY, and opening a Jupyter Notebook

## From EC2 dashboard: AMI setup
Select "Launch Instance"
 - Step 1: Choose an Amazon Machine Image (AMI)
    Select Anaconda with Python 3 in AWS Marketplace
 - Step 2: Choose an Instance Type
     - t2.micro (free tier eligible)

...

 - Step 6: Configure Security Group
     - Select "Add Rule"
         - Type: Custom TCP Rule
         - Port Range: 8888
          - Source: Anywhere (0.0.0.0/0,::/0)
 - Step 7: Review Instance Launch
     - "Launch" with appropriate key

## SSH to instance with PuTTY

 - HostName: ec2-user@<paste_Public_DNS_(IPv4)_here>
 - Port: 22

In catagory panel select SSH dropdown then Auth
 - Browse to key .ppk file
 - Select "Open"
 - Select "Yes" in PuTTY pop up window

## Connect instance to localhost:8888 with PuTTY

 - Right click over "HostName" in upper left corner of PuTTY window
 - Select "Change Settings..." 
 - In PuTTY Reconfiguration pannel select SSH dropdown then Tunnels
    - Source Port: 8888
    - Destination: 127.0.0.1:8888
    - Select "Add"
    - Select "Apply"

## Open Jupyter Notebook in EC2 instance 

### From instance prompt 
$ jupyter notebook

### In browser address bar type the url:
http://127.0.0.1:8888

Accessing the notebook requires a token be entered when prompted in the browser window. The token can be found in the instance window. It is the long alphanumeric found in the web address http://localhost:8888/?token=...


## Open and run Jupyter notebook on hard drive with AMI

Transfer existing jupyter notebook file (Test.ipynb) to instance using the PuTTY Secure Copy Client 

### From the Comand Prompt:
pscp -i C:\<path>\<my-key-pair>.ppk C:\<path>\Test.ipynb ec2-user@<public_dns>:/home/ec2-user/Test.ipynb
confirmation of file transfer will appear
