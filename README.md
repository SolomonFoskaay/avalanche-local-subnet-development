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

Imagine for a second, one of the issues and bottle neck of Blockchains like Ethereum is the all-purpose use which sometimes attract transaction intensive dApps like Play-to-earn- games to deploy on it. 

And as history have it, at peak season, these type of dApps do huge transactions that have several times overwhelmed the Ethereum Blockchain transaction processing capability, caused stuck transactions, increase in gas fees beyond resonable range and eventually rendering the Blockchain less accessible for everyday transactional usage.

What about if those Play-To-Earn games each can have there own Blockchain dedicated to them, seperated from less intensive onchain activities, then it prevent the buttle neck for both the game platform, their users and other general users of the Blockchain. That is precisely what Avalanche Subnets are aiming to solve. 

> <b> [Avalanche Subnets](https://docs.avax.network/subnets#subnets) are dedicated chains for specific use cases all linked together under one main [Avalanche Primary Network](http://support.avalabs.org/en/articles/4135650-what-is-the-primary-network) </b>. 

<br/>
<br/>


## SECTION 2: DEEP DIVE

### Dev Tools Needed To Setup Subnet On Your Local Development Environment

(i) Avalance CLI

(ii) Linux/MacOS (Not available for Windows as at time of publishing this tutorial - For Windows users, a trick is to set Windows SubSystem for Linux or Virtual Machine - both gives you access to Linux OS capabilities on your Windows OS)

NOTE: I will be using Linux for this tutorial (its Ubuntu 20.04 LTS but you should be able to follow using any other Linux distros out there)

(iii) Metamask

(iv) General Programming Knowledge 


<br/>
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
<br/>


### STEP 3: Using The Setup To Demonstrate A Simple ‘hello world’ Local Subnet Creation

It is time to deploy our first sample subnet on Local Server. I will name the Subnet "hello world" (you can choose to name yours anything as desired - feel free to play around)

Create a Subnet named "hello world" - use the "avalanche subnet create" command with your chosen Subnet name (in my case is "helloworld" - avoid using space between the Subnet name to avoid mismatched number of agument/parameter error)
~~~javascript
avalanche subnet create helloworld
~~~

This will trigger a pre-built easy to follow template for you to fill all essential parameters to setup the genesis file for your subnet

NOTE: Genesis file - is a file containing the essential configurations that determines how your Subnet will funtion including gas fees and other features. To customize it beyond the default template provided in the Avalanche CLI for yout project, <b> [see this guide here](https://docs.avax.network/subnets/create-a-local-subnet#create-a-custom-subnet-configuration) </b>

### Some of the questions are:

Have included a video walkthrough below to help incase you get stuck following the text below.

#### Choose your VM (Virtual Machine): 

Core of any Blockchain which determines how code is executed including the programming language that can interact with the Blockchain.

> I pick SubnetEVM (this is reconfigured and means it works with Ethereum Virtual Machine which will allow me to deploy Solidity based smart contract later on)

#### Enter Chain ID: - 

A unique ID for your Blockchain - No two Blockchains can have the same Chain ID. You can use tools like <b> [Chainlist.org](https://chainlist.org/) </b> to check if your choosen chain id is not taken yet, if its taken, your setup will fail to deploy when setting up Subnet for mainnet later down the line.

> I used "1234567890210" (That is insanely long and not recommended - just for sample purpose only)

#### Token symbol:
Selecting a token symbol is same as Bitcoin represented as BTC, Ethereum as ETH and Avalanche as AVAX. Choose your token symbol here for the native token of the Subnet

> I used HWTK (representing Hello World Token)

#### Gas fees:
How much you want to be charging per transaction via your subnet?

> I choose the lowest to align with Avalanche mainnet gas fees structure. You can select higher depending on your Subnet usecase

#### Airdrop initial token
Yeah, you get to choose who gets the initial native token airdrop as desired.

> In this case I go with the sample 1Million airdrop to ensure I have the token to pay for fee on the Subnet once deployed - though this not recommended for mainnet subnet launch

#### Custom precompile:
Want more customization for your Virtual Machine (In our case it the previously selected SubnetEVM). Add it here

> No, not time to customize, so I selected NO - Yeah!

Wahoo, we did it. 

Our Genesis file successfully created for our Subnet

We can now deploy the subnet

LFG



https://user-images.githubusercontent.com/83863629/177012039-9a6733d2-3cd8-4365-aad9-891ddd058620.mp4





<br>
<br/>


### STEP 4: Using The Setup To Demonstrate A Simple ‘hello world’ Local Subnet Deployment

Yeah, its time to deploy our Subnet to the local Avalanche network.

Deploy the "helloworld" Subnet created previously with the following command:
~~~javascript
avalanche subnet deploy helloworld
~~~

### Some of the questions are:

Have also included a video walkthrough below to help incase you get stuck following the text below.

#### Choose a network to deploy on: 

Local Network - Deploy on your own computer (totally free)

Fuji - Testnet (no real money involved but need fake testnet AVAX token to deploy - check AVAX faucet to get some free)

Mainnet - The actual network, cost real money to deploy on 

> I pick Local option since this tutorial is focusing on local deployment (others may be done in the future - so kindly let me know if this tutorial was helpful and need for others too)

NOTE: This could take a while based on your network strenght but mine was done within 3Minutes.

Also, copy and paste the Metamask part in a text  document for later use which includes the wallet where the airdroped token was sent and its private key to access the wallet and fake/test funds later.



https://user-images.githubusercontent.com/83863629/177013665-1e905e99-0145-4b82-8ac1-32aabc0462f6.mp4

Yeah we successfully deployed an "hello world" Subnet on our local Avalanche development network environment.



<br>
<br/>


### STEP 5: Accessing Funded Account(s) In Metamask

Did you remembered when creating the Subnet earlier in step 3 above we [airdrop 1Million of the Subnet native token (1,000,000HWT)](https://github.com/SolomonFoskaay/avalanche-local-subnet-development/blob/main/README.md#airdrop-initial-token) into a wallet generated for us with its private key.

Its time to access it using the RPC configuration generated when it was deployed. I also told you to copy and paste it from the termnal to a text editor for future use.

To make it easier, here is a walkthrough step-by-step videos for you:

(1) Setup Metamask:

If you are new to Metamask setup - I recently did a video on [How To Setup Metamask For Beginners](https://www.youtube.com/watch?v=naCHfcKh25s) - check it out

(2) Add the funded account for our created helloworld Subnet to Metamask

To make it easier, I have done and included a video to guide you below:

https://user-images.githubusercontent.com/83863629/177036333-3da08513-e494-4cbe-b3a0-084a8848524a.mp4




<br>
<br/>


### STEP 6: Deploy Smart Contracts On Subnets

In this step, lets deploy a simple token smart contract on the Hello World Subnet we have been working on.

I will be using [OpenZeppelin token contract creator wizard](https://docs.openzeppelin.com/contracts/4.x/wizard) to create the smart contract without need to code it myself from sratch (also their contracts are audited and used by top web3 platforms for EVM Blockchains).

NOTE: 

If you are new to Smart Contract development using Solidity, then you might want to checkout this course I created for **[absolute beginners to solidity](https://dprogramminguniversity.com/courses/smart-contract-development-with-solidity-for-beginners/)** and its 100% FREE! 


**(1) See The walk through video below to create the contract without coding using OpenZeppelin:**



https://user-images.githubusercontent.com/83863629/177037769-8bda8a60-d908-4c49-9657-55edc42c2ef4.mp4

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.4;

import "@openzeppelin/contracts@4.7.0/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts@4.7.0/token/ERC20/extensions/ERC20Burnable.sol";
import "@openzeppelin/contracts@4.7.0/access/Ownable.sol";

contract MySubnetToken is ERC20, ERC20Burnable, Ownable {
    constructor() ERC20("MySubnetToken", "MSTK") {
        _mint(msg.sender, 20000 * 10 ** decimals());
    }

    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }
}
```



<br>


**(2) Deploy the smart contract to the hello world Subnet EVM Blockchain on our local environment**

Yeah, once the smart contract is ready, its time to deploy it 

Follow the walkthrough video have done for you using **[Remix](https://remix.ethereum.org/)** below:

https://user-images.githubusercontent.com/83863629/177038927-4744c0f0-4efa-4724-bf9e-63e4d273677b.mp4


Congrats we now have our Subnet Blockchain accepting solidity based Smart contract

In next step we will attempt to interact with the smart contract after deployment






<br>
<br/>


### STEP 7: Interact With Smart Contracts On Subnets

In this step, lets interact with the token smart contract deployed on the hello world Subnet.

**(1) Add the custom token generated by the contract to Metamask**

Let's add the MSTK to display in Metamask using the contract address generated after deployment on the Subnet 

> 0x17aB05351fC94a1a67Bf3f56DdbB941aE6c63E25


https://user-images.githubusercontent.com/83863629/177042567-c44b2a76-fe77-45c4-a4a7-0bc0d01a237b.mp4



**(2) Mint more custom tokens from the contract** 

Another interaction with the contract will be to create more MSTK tokens.

Initially when deploying the contract, we minted just 20,000MSTK. 

Now, let's mint 30,000MSTK more using the "Mint" function in the contract (without the mint function added beore deployment, it will be impossible for us to mint more tokens now or later after deployment)

After minting, the Total Supply of the token will increase from 20,000MSTK to 50,000MSTK

Lets go....

https://user-images.githubusercontent.com/83863629/177043972-d7310977-8268-4d96-bb37-e7d4f64c2084.mp4




**(3) Transfer the custom tokens from one wallet to another** 

Let's do a simple transfer of "5,000MSTK" from the wallet used to deploy the token to another wallet to confirm the token contract is working fine on the Subnet Blockchain.


https://user-images.githubusercontent.com/83863629/177044277-017b08bb-9500-4104-9d18-92af0431be54.mp4








## SECTION 3: CONCLUSSION

### Troubleshoot common issues

You may face different issues. 

Some common ones I experienced are:

**(i) CURL error - **

Which has solved earlier in this totorial

**(2) When deploying the Subnet, the network may not start. **

One of the causes could be that you already have an instance of another previously deployed Subnet still active on your computer. To solve that simple use the commond below:
```Javascript
avalanche network clean
```
and I got the following output:
```
foskaay@Foskaay-N750JV:~/bin$ avalanche network clean
No local network running
Process terminated.
```

For other issues, you can go through helpful guide from Avanlanche Subnet documentation in the additional resources below.


### Additional Resources

[Create Local Subnet](https://docs.avax.network/subnets/create-a-local-subnet)

[Avalanche Network Code](https://docs.avax.network/subnets/create-a-local-subnet#network)




