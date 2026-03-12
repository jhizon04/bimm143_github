## Basic Unix

Some important file system commands include 

pwd: Print working directory 
ls: list files and folders
cd: change directory 
mkdir: Make a new directory 
rm: Delete files and directions** 
nano: A very basic text editor that is always available 
less: To view/read text files page by page (pager program)

My AWS instance: 
ssh -i ~/Downloads/bimm143_jh.pem ubuntu@ec2-18-236-85-40.us-west-2.compute.amazonaws.com

## Class 17 AWS instance address
ssh -i "~/Downloads/bimm143_jh.pem" ubuntu@ec2-34-216-203-194.us-west-2.compute.amazonaws.com 

## Class 17 to copy from AWS instance

scp -r -i "~/Downloads/bimm143_jh.pem" ubuntu@ec2-34-216-203-194.us-west-2.compute.amazonaws.com:~/*_quant .


IF on a different IP, the @ will be different

To copy from my AWS instance 
scp -i ~/Downloads/bimm143_jh.pem ubuntu@ec2-18-236-85-40.us-west-2.compute.amazonaws.com:~/work/results.tsv .