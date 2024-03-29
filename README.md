# Module 12 - Beginner Lab: Creating and setting up a Hyperledger Fabric blockchain using Amazon Managed Blockchain

## Background

## Meta Information
| Attribute | Explanation |
| - | - |
| Summary | This lab goes over the creation of a Hyperledger Fabric instance and other configuration settings to begin |
| Topics | AWS, blockchain, production |
| Audience | CS1 and above |
| Difficulty | Beginner |
| Strengths | Amazon does a great job at covering the tutorial, information about every step is written here |
| Weaknesses | tbw |
| Dependencies | Internet connection to aws.amazon.com and a modern web browser |
| Variants | Amazon is going to release an Ethereum framework soon |

## Overview on Amazon product dependencies
* Amazon Managed Blockchain - Hyperledger Fabric 1.2 
* Amazon EC2 virtual machine - Amazon Linux EC2 virtual machine
* Amazon VPC - Virtual Private Cloud to link the EC2 client with the Hyperledger Fabric blockchain

## Assignment Instructions (2.5 - 3 Hours)
### Create an AWS account for cloud services
1. First, you must create an AWS account in order to use Amazon Managed Blockchain and other services. [You can make an account here.](https://aws.amazon.com/resources/create-account/)

### Step one: Create the Network and First Member
* Follow [these instructions](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/get-started-create-network.html)
* This step will create the Network and populate it with the first member. A blockchain network is deleted once all members leave the network.

### Step two: Create an Endpoint
* Follow [these instructions](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/get-started-create-endpoint.html)
* Now that the network is up and running in your VPC, you set up an interface VPC endpoint (AWS PrivateLink) for your member. This allows the Amazon EC2 instance that you use as a Hyperledger Fabric client to interact with the Hyperledger Fabric endpoints that Amazon Managed Blockchain exposes for your member and network resources.  

### Step three: Create an Amazon EC2 Instance and Set Up the Hyperledger Fabric Client
1. Create a new instance of Amazon EC2 with the same VPC and security groups as the VPC endpoint created in step two. An additional inbound rule must be added for SSH access on port 22. [See the following document on how to create an Amazon EC2 instance](https://docs.aws.amazon.com/efs/latest/ug/gs-step-one-create-ec2-resources.html)
2. In the EC2 AWS interface with all your instances, connect to your EC2 instance by clicking on "Connect" and selecting "EC2 instance connect."
![EC2 connect](/res/EC2_connect.PNG)
![EC2 SSH](/res/EC2_SSH.PNG)
3. `awscli` needs to be updated. If you do not have awscli to the latest version, you wont be able to run some commands that interact with the blockchain. Run the following:
* ``sudo yum install python2-pip``
* ``sudo pip install awscli --upgrade``

`awscli` must also be configured. This uses your AWS security credentials found in the following page:
![AWS security](/res/access_keys.PNG)
You will need to create a new set of access keys, as the root IDs cannot show their secret key. This can be done by clicking on "Create New Access Key." Run the following command:
``aws configure``
* The first two prompts will ask for your ID and your secret key
* The third will ask for your region, `us-east-1` will do the job
* The fourth will ask for your default output format, `json` is what we want
* When done, your command prompt should look like this:
![aws configure](/res/aws_configure.PNG)
4. *THIS IS NOT A STEP! IT'S FOR INFORMATION ONLY* Do not do run this command yet, but do pay close attention when you get to it, as the arguments in red have to be replaced with the ones in your Amazon Managed Blockchain dashboard:
![args_attention](/res/args_attention.PNG)
![n_arg](/res/n_arg.PNG)
![m_arg](/res/m_arg.PNG)
Running the command should give you a similar output:
![CA endpoint](/res/ca_endpoint.PNG)
Pay close attention to the box in blue when following the instructions.
5. Follow [these instructions](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/get-started-create-client.html)

### Step four: Enroll the Member Admin
* When typing directory paths, be sure that the path is full and that there are no relative paths. Some commands will not work with relative paths.
* If you have any special characters in your password, when executing any command that requires a password to be typed in, make sure to wrap the password 'like this'
* Follow [these instructions](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/get-started-enroll-admin.html)

### Step five: Create a Peer Node
* Your member's peer nodes interact with other members' peer nodes on the blockchain to query and update the ledger, and store a local copy of the ledger.
* Follow [these instructions](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/get-started-create-peer-node.html)

### Step six: Create a Channel
* Before you begin run the following command:
`` wget https://raw.githubusercontent.com/UHMC/module-12-lab-beginner/master/configtx.yaml``
	* The configtx.yaml file that docker reads is sensitive to whitespaces and other formatting changes. Pasting the configuration onto a new file might throw errors. This repository has that boilerplate configuration file formatted properly for your convenience. All that's left to do is edit it as the tutorial states.
* When adding the `PEER` variable to your `.bash_profile` make sure that you are copying the peer endpoint and NOT the peer event endpoint:
![peer endpoint](/res/peer_endpoint.PNG)
* Follow [these instructions](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/get-started-create-channel.html)
### Step seven: Run Chaincode
* This is where you actually execute code on the blockchain. 
* Follow [these instructions](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/get-started-chaincode.html)

### Step eight: Invite a Member and Create a Joint Channel
* [This step is not necessary for the purposes of this tutorial, but on a production system, adding other AWS members to a channel is important](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/get-started-joint-channel.html)


## Credits
Dr. Debasis Bhattacharya  
Mario Canul  
Saxon Knight  
