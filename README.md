# Getting Started with Teal (workshop) 🎇🤩

This repository forms part of a introduction to development in [TEAL](https://developer.algorand.org/docs/get-details/dapps/avm/teal/) and [PYTEAL](https://pyteal.readthedocs.io/en/stable/) explained also in these [Slides](https://docs.google.com/presentation/d/10gSTn77q41u_AKdGSNYvbzWZigFDtO23uTr8vJYN94s/edit?usp=sharing).

**Resources:**
- [Simple Teal](https://developer.algorand.org/docs/get-details/dapps/smart-contracts/smartsigs/walkthrough/?from_query=smart%20sig#simple-teal-example) (From Algorand).
- [AMM Repo](https://github.com/gpylypchuk/DeFi-AMM) (Mio).
- [Explorer](https://app.dappflow.org/explorer/home)
- [All of Algorand](https://awesomealgo.com/)

This Repository is still under construction 👷‍

Next weeks it will be upgrated to explain how to create your own [AMM in PyTeal](https://github.com/dspytdao/Algo_AMM) 😋

# Teal 😵
Below there are the steps to follow and test by yourself a smart signature.

## 1. Instalation
Before start, you need to have instaled [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) (only if you are in Windows), Docker ([Windows](https://learn.microsoft.com/en-us/windows/wsl/tutorials/wsl-containers), [Mac](https://docs.docker.com/desktop/install/mac-install/)) and the Sandbox.

In a folder:
```bash
git clone https://github.com/algorand/sandbox
git clone https://github.com/gpylypchuk/workshop-intro-teal
```

### Start the Sandbox
This command will init the containers.
```bash
./sandbox/sandbox up
```

## 2. Copy the contract to the Sandbox
Posisionated inside the multisig sample folder:
```bash
../sandbox/sandbox copyTo simple.teal
```

Now you have copied the contract. To interact with it in the development environment you have to start the Algorand Develoment console.
```bash
../sandbox/sandbox enter algod
```

## 3. Compile it 🤯
When you're inside Algorand Develomnet environment, the next step is compile it. Here it comes the delegated signature!
```bash
# The '-o' indicates output
# The '-a' indicates address
# The '-d' indicates directory
goal clerk compile simple.teal -o mydelegatedsig.lsig -s -a YOUR_DELEGATED_ADDRESS -d .
```

## 4. Send a transaction
Now, you have compiled the code. The next step is test it 🧐
Send a transaction from your delegated address.
```bash
# The '-f' indicates from (sender)
# The '-a' indicates amount in microalgos
# The '-t' indicates to (receiver)
# The '-L' indicates load
goal clerk send -f YOUR_DELEGATED_ADDRESS -a 100000 -t ANOTHER_ADDRESS -L mydelegatedsig.lsig -d .
```

## Congratulations 🎉
You have sent a transaction by another delegated address!

# Pyteal 🐍
Here we will compile a contract in PyTeal

## 1. Instalation
Initialize your virtual environment (go to pyteal-contracts)
```bash
python3 -m venv venv
source ./venv/bin/activate
```

### Install requirements
To do this type:
```bash
pip install -r requirements.txt
```

## 2. Compile it ✨
Easy!, now you can compile the sample contract typing

```bash
./build.sh contracts.counter.step_01
```

## Congratulations 🥳
You have compiled it.

So, you should have the approval.teal and clear.teal inside the folder `build`

Now, you can use the steps we discuss before to interact with the Teal contract transpiled.
