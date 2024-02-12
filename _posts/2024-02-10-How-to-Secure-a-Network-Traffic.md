---
layout: post
title: How to Secure a Network Traffic
subtitle: Read Me
categories: Azure Network
tags: [Azure, VirtualMachines, blog, vm, NetworkSecurityGroup,IPAddress, RDP, SSH, NSG]
---

## How to Secure a Network Traffic


### Introduction

I wants to secure a Network Traffic to ensure that access to virtual machines is restricted. To do this, I need to:
* 		Create and configure network security groups.
* 		Associate network security groups to virtual machines.
* 		Deny and allow access to the virtual machines by using network security groups.

### To create a secure network, there are 4 main steps we will take:

- Create a virtual machine.
- Create a network security group(NSG)
- Configure an inbound security port rule to allow Remote Desktop Protocol (RDP)
- Configure an outbound security port rule to deny internet access 


### Create a virtual machine(VM).

I want to create a virtual machine.

1. From the Azure Portal click “All Services”
2. Click “Virtual Machines”
3. Click on “Create ” and choose “Virtual machine”
4. On the Basic Tab in the “Resource group” input. 
    - If you don’t have a resource group, click create resource group and provide a name for the resource group. 
    - If you already have one input in.
  5. Fill in your virtual machine name on the “Virtual machine name” input.
  6. Leave every other info as default.
  7. Scroll down to “Create a virtual machine”
	- Input your username
	- Password
	- Confirm Password
8. On the “Public inbound ports” select none and proceed to Networking tab with two clicks on the next button.
9. On the “NIC network security group” choose “”None
10. Click “Next” twice to “Monitoring”. On the “Boot diagnostics” click “Disable”
11. Leave default and click “Review and Create”
12. Click “create” to create a new VM
13. When deployment complete, scroll down and “Go to resource”
14. On the VM, scroll to “Networking”, and click “Network Setting”
15. Copy the network interface, because you will need it.
 
 ![datacamp certification](/assets/images/securedVM/VM.jpeg)

### Create a network security group

1. From the Azure Portal click “All Services”
3. Search for and select “network security group”
4. Click on “Create ” and fill in the details.
5. Click “review and create” and click “create”
6. When its completed click “go to resource”

 ![datacamp certification](/assets/images/securedVM/NSG.jpeg)

7. On the NSG page go scroll the “Network interface” and click on it

 ![datacamp certification](/assets/images/securedVM/networkinterface.jpeg)

8. Next, click “associate” on the tab

 ![datacamp certification](/assets/images/securedVM/associatenetworkinterface.jpeg)

9. Click the “Network interface association” dropdown arrow

 ![datacamp certification](/assets/images/securedVM/associatenetworkinterface2.jpeg)

10. Select the network interface and click “OK”

 ![datacamp certification](/assets/images/securedVM/associatenetworkinterfacesucessful.jpeg)


### How to allow an RDP traffic to the virtual machine by configuring an inbound security port rule

By default NSG does not allow RDP. So we need to configure an inbound security rule to allow RDP

1. Go back to your already created virtual machine and click on “Network Setting”
2. Select the “create port rules” and choose “inbound port rule”

 ![datacamp certification](/assets/images/securedVM/createinboundrule.jpeg)

3. Input a “Destination port ranges” and a “priority”
4. Select “TCP”
5. Add a “name”
6. Click ”Add“

 ![datacamp certification](/assets/images/securedVM/sucessinboundrule.jpeg)

How to connect to RDP

1. Go to the “Overview” of the VM
2. Click on “Connect”
3. Click on “Download RDP File”

 ![datacamp certification](/assets/images/securedVM/connectrdp.jpeg)

4. Download, input details and continue
5. There you go, your VM is ready.

 ![datacamp certification](/assets/images/securedVM/displayVM.jpeg)


### Configure an outbound security port rule to deny internet access

1. Go to your VM and click on “Network Setting”
2. Select the “create port rules” and choose “outbound port rule”

 ![datacamp certification](/assets/images/securedVM/createoutboundrule.jpeg)

3. On destination input, “Service Tag”
4. On “Destination port ranges” put “*” which means all ports
5. On ”Protocol” select “TCP”
6. On “Action” select “Deny”
7. Input a high Priority

 ![datacamp certification](/assets/images/securedVM/outboundruleform.jpeg)

8. Add name and click on “Add”
9. Return to your RDP session and try to open a website , you will notice its not opening, because access has been denied.

 ![datacamp certification](/assets/images/securedVM/deniedrdp.jpeg)
