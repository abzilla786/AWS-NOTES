Setting up an EC2 server:

AMI - Ubuntu Server 18.04 LTS (HVM), SSD Volume Type

Instance - t2.micro

Configure Instance - Network - DevOpsStudent - Subnet - DevOpsStudentSubnet

Add Storage - skip
```
Add Tags - {"Name", "ash-eng54-first-ec2"} {"Cohort", "Eng54"}
```

Connect to ports: 80, 22, 8080, 443, 3000, each of which only accessible from "my IP", to prevent unauthorised access.

Create a key and save it to the .ssh folder on your machine.

Accessing the server
```
ssh -i <location of .pem> ubuntu@<ip>
```

-i refers to the "identity file", which is the key that you use to connect to the AWS server.

<location of .pem> - this is the absolute path to the key, which is likely saved at ~/.ssh You will also need to include the name of the actual file

the referred to at the end is the IPv4 IP of the AWS machine.

Copying a file from your machine ontp the AWS machine
```
scp -i path/to/key file/to/copy <user>@ec2-xx-xx-xxx-xxx:path/to/file
```
scp stands for Secure CoPy.

the path/to/key is the .pem key referred to in the previous section

the file/to/copy is your the file on your machine

refers to the VM's user name - in our case it was "Ubuntu" - check in /home/ on the VM

You then need to replace xx-xx-xxx-xxx with your VM IP address.

Finally, the path/to/file is the location you want to place the file

rsync
```
rsync -r dir1/ dir2
```
Rsync is used to sync directories together, keeping one appearing the same as the other.

-r is "recursive", which is required for directory sharing - this will make sure each file is sent to the new location.

You also need to place the absolute path for each path afterwards, making sure that the "from" location ends with a training / as this refers to the contents of that folder.
