# UUPS Proxy Pattern

The UUPS Proxy Pattern is another way to separate responsibilities between Proxy and Implementation contracts. In this case, the ```upgradeTo``` function is also part of the Implementation contract, and is called using a delegatecall through the Proxy by the owner.

In UUPS whether its the admin or the user, all the calls are sent to the Implementation Contract The advantage of this is that every time a call is made we will not have to access the storage to check if the user who started the call is an admin or not which improved efficiency and costs. Also because its the Implementation Contract you can customize the function according to your need by adding things like Timelock, Access Control etc with every new Implementation that comes up which couldn't have been done in the Transparent Proxy Pattern

# Issues with UUPS Proxy Pattern

The issue with this is now because the ```upgradeTo``` function exists on the side of the Implementation contract developer has to worry about the implementation of this function which may sometimes be complicated and because more code has been added, it increases the possibility of attacks. This function also needs to be in all the versions of Implementation Contract which are upgraded which introduces a risk if maybe the developer forgets to add this function and then the contract can no longer be upgraded.

# Sample Hardhat Project

This project demonstrates a basic Hardhat use case. It comes with a sample contract, a test for that contract, and a script that deploys that contract.

Try running the following tasks:

```shell
npx hardhat help
npx hardhat test

```
