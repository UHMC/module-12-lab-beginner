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

## Assignment Instructions
### Create an AWS account for cloud services
1. First, you must create an AWS account in order to use Amazon Managed Blockchain and other services. [You can make an account here.](https://aws.amazon.com/resources/create-account/)

### Step one: Create the Network and First Member
* Follow [these instructions](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/get-started-create-network.html)
* This step will create the Network and populate it with the first member. A blockchain network is deleted once all members leave the network.

### Step two: Create an Endpoint
* Follow [these instructions](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/get-started-create-endpoint.html)
* A VPC endpoint is necessary to allow an Amazon EC2 instance to be used as a Hyperledger Fabric client to interact with Hyperledger Fabric endpoints that Amazon Managed Blockchain exposes for your member and network resources. 

### Step three: Create an Amazon EC2 Instance and Set Up the Hyperledger Fabric Client
1. Create a new instance of Amazon EC2 with the same VPC and security groups as the VPC endpoint created in step two. An additional inbound rule must be added for SSH access on port 22. [See the following document on how to create an Amazon EC2 instance](https://docs.aws.amazon.com/efs/latest/ug/gs-step-one-create-ec2-resources.html)
2. In the EC2 AWS interface with all your instances, connect to your EC2 instance by clicking on "Connect" and selecting "EC2 instance connect."
![EC2 connect](/res/EC2_connect.PNG)
![EC2 SSH](/res/EC2_SSH.PNG)
3. 
### Step four: Enroll the Member Admin
* Follow [these instructions](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/get-started-enroll-admin.html)

### Step five: Create a Peer Node
* Follow [these instructions](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/get-started-create-peer-node.html)

### Step six: Create a Channel
* Follow [these instructions](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/get-started-create-channel.html)

### Step seven: Run Chaincode
* Follow [these instructions](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/get-started-chaincode.html)

### Step eight: Invite a Member and Create a Joint Channel
* Follow [these instructions](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/get-started-joint-channel.html)


## Credits
Dr. Debasis Bhattacharya  
Mario Canul  
Saxon Knight  
