
##### Download aws keypair file

You can generate and download keypair this [way.](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html)

##### Edit group_vars/all.yml

```
ansible_ssh_private_key_file: ./your_keypair.pem #change this to your ssh-keypair file path
aws_access_key: "your_access_key" #change this to your your_access_key
aws_secret_key: "your_secret_key" #change this to your your_secret_key
ec2_keypair: "your_keypair" #change this to your ssh-keypair file name
ec2_instance_type: "t2.medium" #change this to your instance type
ec2_image: "ami-005ca2b3c05cf85e2" #change this to Fedora-Cloud-Base-27-20180622.0.x86_64-hvm AMI ID for your AWS region
ec2_region: "us-east-1" #change this to your ec2_region id
ec2_vpc_id: "" #change this to your ec2_vpc_id

```

##### For Ubuntu 16.04 install and configure ansible like this

```
apt get update && apt-get -y install python3-pip openssl libssl-dev
pip3 install ansible
pip3 install --upgrade cryptography
```
##### Run deployment for swifty.lite

```
ansible-playbook -vv -i localhost lite.yml
```
