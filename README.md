This repository deploys a config management server ( ansible server) and then deploys
a wordpress stack. Please refer [deploy-wordpress-aws](https://github.com/ajinkyakadam/deploy-wordpress-aws)
for the wordpress cloudformation template.


### Instructions to Use (For Linux-Ubuntu Users)

Lets first create a keypair by logging into our amazon console. Remember the name of the keypair.
We will use the created keypair to ssh into ec2 instances.
**Note** : The stack by default uses a keypair named `staticsitestack`. Please make
sure you change it.

Next lets setup the credentails which we will use to provision resources. You need the `access_key` and `secret_access_key`
Create a folder name `.aws` in your home directory, using the following command

```
mkdir ~/.aws/
```

Next create `credentails` file in `~/.aws/` folder, using

```
touch credentails
```

Now lets add our keys to the credentials file. Replace `your_access_key` and `your_secret_access_key` with the keys provided to you. Add these lines in your credentials file.

```
[default]
aws_access_key_id=your_access_key
aws_secret_access_key=your_secret_access_key
```


Add the following to file `/etc/ansible/hosts`

```
[local]
localhost
```


Then download this repository by running,

```
git clone https://github.com/ajinkyakadam/ansibleserverCF.git
```

Next navigate to the repository directory,

```
cd ansibleserverCF
```

Now to deploy ansible server and wordpress stack run

```
ansible-playbook -i /etc/ansible/hosts deploy-ansible-wp-stack.yml --verbose
```
