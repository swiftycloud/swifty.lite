
##### Download aws keypair file

You can generate and download keypair this [way.](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html)

##### Create aws credential file and add access and secret keys:

```
mkdir ~/.aws/
vim ~/.aws/credentials

[default]
aws_access_key_id=your_key
aws_secret_access_key=your_key
```

##### Edit group_vars/all.yml

```
ansible_ssh_private_key_file: ./your_keypair.pem #change this to your ssh-keypair file path
ec2_keypair: "your_keypair" #change this to your ssh-keypair file name
ec2_instance_type: "t2.medium" #change this to your instance type
ec2_image: "ami-005ca2b3c05cf85e2" #change this to Fedora-Cloud-Base-27-20180622.0.x86_64-hvm AMI ID for your AWS region
ec2_region: "us-east-1" #change this to your ec2_region id
ec2_vpc_id: "your_ec2_vpc_id" #change this to your ec2_vpc_id

```

##### For Ubuntu 16.04/Ubuntu 18.04 install and configure ansible like this

```
sudo apt-get update && sudo apt-get -y install python3-pip openssl libssl-dev ansible
pip3 install ansible
pip3 install --upgrade cryptography
```

##### Run deployment for swifty.lite

```
ansible-playbook -vv -i localhost lite.yml
```