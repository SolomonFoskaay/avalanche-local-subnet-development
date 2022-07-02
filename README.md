# avalanche-local-subnet-development
A Beginner Friendly Step-By-Step Guide To Create /Deploy Subnets on Avalanche Locally For Developers

# How To Set Up Your Development Environment For Local Subnet Development

## SECTION 1: INTRODUCTION

What You Will Learn In This Tutorial?

You will discover what Avalanche Subnets are and how to set it up in your local development environment. This literarily means at the end of this tutorial you will be able to have your own EVM compactible Blockchain deployed to your local server(Thanks to the power of Avalanche Blockchain), using its own native token for gas fees, own custom chain ID, connect to metamask, ready to take smart contract deployed on it and a lot more.

Though, I will try my best to ensure this is as beginner friendly as possible, yet, basic/general programming concept knowledge is of advantage. This is not meant to be first tutorial to take for absolute beginners to Programming fundamentals.

So, if you are ready lets get started. 

### What Is Avalanche?

Avalanche is a network of Blockchains aimed at solving the issues around scalability faced by decentralized Blockchains like Ethereum. Avalance aim to achieve this without sacrificing security and decentralization.

It is currently made up of three (3) chains.

<b> [X-Chain](https://docs.avax.network/overview/getting-started/avalanche-platform#exchange-chain-x-chain) </b>  - Handles Exchanges

<b> [C-Chain](https://docs.avax.network/overview/getting-started/avalanche-platform#contract-chain-c-chain) </b>  - Handles Contracts development on Avalanche network

<b> [P-Chain](https://docs.avax.network/overview/getting-started/avalanche-platform#platform-chain-p-chain) </b>  - Platform Chain handles validators and more.

<b> [Learn More About Avalance Blockchain Structures Here](https://docs.avax.network/overview/getting-started/avalanche-platform) </b>



### What Is Subnet?

In a simple term, Subnet is a laser targeted/niche focused Blockchain which is part of the overall huge Avalanche main chain network. This makes it possible for individuals, coporate organizations and even government to deploy their own Blockchain with full control of the fees structure, privacy, contents allowed, KYC and more without been limited by the main Avalanche Blockchain network.
This innovation is indeed the beginning of a new chapter to lasting scalability solution.

Imagine for a second, one of the issues and bottle neck of Blockchains like Ethereum is the all-purpose use which sometimes attract transaction intensive dApps like Play-to-earn- games to deploy on it. And as history have it, at peak season, these type of dApps do huge transactions that have several times overwhelmed the Ethereum Blockchain transaction processing capability, caused stuck transactions, increase in gas fees beyond resonable range and eventually rendering the Blockchain less accessible for everyday transactional useage.

What about if those Play-To-Earn games each can have there own Blockchain dedicated to them, seperated from less intensive onchain activities, then it prevent the buttle neck for both the game platform, their users and other general uses of the Blockchain. That is precisely what Avalanche Subnets are aiming to solve. 

> <b> [Avalanche Subnets](https://docs.avax.network/subnets#subnets) are dedicated chains for specific use cases all linked together under one main [Avalanche Primary Network](http://support.avalabs.org/en/articles/4135650-what-is-the-primary-network) </b>. 

<br/>
<br/>


## SECTION 2: DEEP DIVE

### Dev Tools Needed To Setup Subnet On Your Local Development Environment

(i) Avalance CLI

(ii) Linux/MacOS (Not available for Windows as at time of publishing this tutorial - For Windows users, a trick is to set Windows SubSystem for Linux or Virtual Machine - both gives you access to Linux OS capabilities on your Windows OS)

NOTE: I will be using Linux for this tutorial (its Ubuntu 20.04 LTS but you should be able to follow using any other Linux distros out there)

(iii) General Programming Knowledge 

<br/>

### STEP 1: Downloading Needed Packages

You don't actually need much packages due to how easy Avalanche team has made this for developers with the Avalanche CLI (lots have been bundled in there to make devs life easier - interesting and kudos to the Avalanche team for this)

If your Linux installation is old (meaning you have been using it for development in the past), then you are almost already set. But, if your Linux installation is fairly new (like mine, sincerely this was my first time of using full stand alone Linux, do use it previously on Windows via WSL but decided to go all in to Linux to actually see how easy it could be to setup Subnets and I was completely blown away how easier it end up been for first time Linux user like me to setup Subnet on local environment- so, you can do it too following this tutorial).


As a new Linux OS user, I got error when tryng to download needed packages but the fix is simple,

Error: 
> command "curl" not found

<img src="https://github.com/SolomonFoskaay/avalanche-local-subnet-development/blob/main/images/Deploy-Avalanche-Subnet-Locally-Images-001a-Error-CURL.png" width="75%" height="75%">


Fix: run this command in terminal:
~~~javascript
sudo apt install curl
~~~

<img src="https://github.com/SolomonFoskaay/avalanche-local-subnet-development/blob/main/images/Deploy-Avalanche-Subnet-Locally-Images-001b-Install-CURL.png" width="75%" height="75%">

Once that confirmed to be on your Linux machine, its time to download needed packages for Subnet setup locally.

<br/>

### STEP 2: Installation Procedures

(i) Open Terminal - Shortcut is Ctrl+Alt+T

(ii) Run following command:
~~~javascript
curl -sSfL https://raw.githubusercontent.com/ava-labs/avalanche-cli/main/scripts/install.sh | sh -s
~~~



https://user-images.githubusercontent.com/83863629/177008366-b6bbde22-28a2-4611-ad38-d9f7dcad5df8.mp4



NOTE: This will install the Avalanche CLI packages and depencies in "./" path. If you want it to be in a custom path, you can do that following <b> [the guide here](https://docs.avax.network/subnets/create-a-local-subnet#installing-in-custom-location) </b>


(iii) Add Binary to path with following commands
~~~javascript
cd bin
~~~


Then,
~~~javascript
export PATH=$PWD:$PATH
~~~


(iv) Check Avalanche folder setup
To confirm if our above steps downloaded and installed neccessary packages and dependencies in a folder called Avalanche, run this command
~~~javascript
ls
~~~
It should show "Avalanche" folder



https://user-images.githubusercontent.com/83863629/177009403-e6ad2f56-5f13-473e-9447-3e505fb576f2.mp4




<br/>

### STEP 3: Using The Setup To Demonstrate A Simple ‘hello world’ Local Subnet Deployment

It is time to deploy our first sample subnet on Local Server. I will name the Subnet "hello world" (you can choose to name yours anything as desired - feel free to play around)

(i) Create a Subnet named "hello world" - use the "avalanche subnet create" command with your chosen Subnet name (in my case is "hello world")
~~~javascript
avalanche subnet create hello world
~~~

This will trigger a pre-built easy to follow template for you to fill all essential parameters to setup the genesis file for your subnet

NOTE: Genesis file - is a file containing the essential configurations that determines how your Subnet will funtion including gas fees and other features. To customize it beyond the default template provided in the Avalanche CLI for yout project, <b> [see this guide here](https://docs.avax.network/subnets/create-a-local-subnet#create-a-custom-subnet-configuration) </b>

#### Some of the questions are:

#### Choose your VM (Virtual Machine): 

Core of any Blockchain which determines how code is executed including the programming language that can interact with the Blockchain.

> I pick SubnetEVM (this is reconfigured and means it works with Ethereum Virtual Machine which will allow me to deploy Solidity based smart contract later on)

#### Enter Chain ID: - 

A unique ID for your Blockchain - No two Blockchains can have the same Chain ID. You can use tools like <b> [Chainlist.org](https://chainlist.org/) </b> to check if your choosen chain id is not taken yet, if its taken, your setup will fail to deploy when setting up Subnet for mainnet later down the line.

> I used "1234567890210" (That is insanely long and not recommended - just for sample purpose only)




Troubleshoot common issues

Add node validators to the subnet

Access funded accounts

Deploy smart contracts

Interact with contracts

Bonus point: explain how to experiment with different customization by creating/tearing down/recreating


SECTION 3: CONCLUSSION
