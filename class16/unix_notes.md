## Core Unix commands 

Most unix commands have super short names, which makes them quick to type but annoying to learn. Major file system related commands include:

pwd:   Print working directory
ls:    List files and directory
cd:    Change directory 
mkdir: Make a new directory
rm:    Remove files and directory
cp:    Copy files (source > destination)
mv:    Move files or directories (basically re-name)
nano:  A text editor (very basic but always available) 

curl: Download files from web or ftp
wget: Download files from the web
tar:  -zxvf :UnTar (unpackage) Tar archive files
gunzip: UnZip files
$PATH:  The places (dirs) to look for programs

## AWS EC2 Instance

Connect to my instance with:

ssh -i ~/Downloads/bimm143_ikish.pem ubuntu@ec2-54-245-0-214.us-west-2.compute.amazonaws.com

Secure Copy files between machines, in this case from our instance to our laptop

scp -i ~/Downloads/bimm143_ikish.pem ubuntu@ec2-54-245-0-214.us-west-2.compute.amazonaws.com:/home/ubuntu/work/bimm143_github/class16/results.txt ./ 


## Class 17 instance
ssh -i ~/Downloads/ls]bimm143_ikish.pem_ubuntu@ec2-52-26-129-115.us-west-2.compute.amazonaws.com

export KEY=~/Downloads/bimm143_ikish.pem
export SERVER=ubuntu@ec2-52-26-129-115.us-west-2.compute.amazonaws.com

ssh -i $KEY $SERVER




