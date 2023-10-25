# Setting up an Azure Virtual Machine

## First we can take a look at the structure of a virtual machine on Azure:

![Alt text](VMonAzureDiagram.png)

## In order to set up a VM we could follow these steps:


## Step 1 - Select Create a Virtual Machine in the search bar or from the resource group as it is a resource

SettingUpAzureVM.md ![Alt text](AzureVirtualMachine1.png) ![Alt text](AzureVirtualMachine2.png)

## Step 2 - Select the details of the VM including resource group and availability zones. Here we can also select the secturity type for the chosen image, in this case Ubuntu Pro 18.04 LTS
![Alt text](AzureVirtualMachine3.png)
![Alt text](AzureVirtualMachine4.png)

## Step 3 - Select the standard disk size

![Alt text](AzureVirtualMachine5.png)

## Step 4: Select the Public IP and Basic Network security Groups
![Alt text](AzureVirtualMachine6.png)

## Step 5: Input user data from provision file to install App
![Alt text](AzureVirtualMachine7.png)
