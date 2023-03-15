We have an existing website running on a local Ubuntu Linux server. Our goal is to create an Azure virtual machine (VM) using the latest Ubuntu image and then migrate the site to the cloud. In this unit, you'll learn about the options you'll need to evaluate when creating a virtual machine in Azure.

## Introduction to Azure Virtual Machines

Azure Virtual Machines are an on-demand, scalable cloud-computing resource. They include processors, memory, storage, and networking resources. You can start and stop virtual machines at will and manage them from the Azure portal or with the Azure CLI. You can also use a remote Secure Shell (SSH) to connect directly to the running VM and execute commands as if you were on a local computer.

### Run Linux in Azure

Creating Linux-based VMs in Azure is easy. Microsoft has partnered with prominent Linux vendors to ensure their distributions are optimized for the Azure platform. You can create virtual machines from prebuilt images for a variety of popular Linux distributions, such as SUSE, Red Hat, and Ubuntu, or build your own Linux distribution to run in the cloud.

## Create an Azure VM

VMs can be defined and deployed on Azure in several ways: the Azure portal, a script (using the Azure CLI or Azure PowerShell), or an Azure Resource Manager template. In all cases, you'll need to supply several pieces of information that we'll cover shortly.

The Azure Marketplace also provides preconfigured images that include both an OS and favorite software tools installed for specific scenarios.

![Screenshot of the Azure portal showing several virtual machine options in the Azure Marketplace.](https://learn.microsoft.com/en-us/training/modules/create-linux-virtual-machine-in-azure/media/2-marketplace-vm-choices.png)

## Resources used in a Linux VM

When creating a Linux VM in Azure, you also create resources to host the VM. These resources work together to virtualize a computer and run the Linux operating system. These resources must exist (and be selected during VM creation), or they'll be created with the VM:

-   A virtual machine that provides CPU and memory resources
-   An Azure Storage account to hold the virtual hard disks
-   Virtual disks to hold the OS, applications, and data
-   A virtual network (VNet) to connect the VM to other Azure services or your on-premises hardware
-   A network interface to communicate with the VNet
-   An optional public IP address so you can access the VM

Like other Azure services, you'll need a **Resource Group** to contain the VM (and optionally group these resources for administration). When you create a new VM, you can either use an existing resource group or create a new one.

## Choose the VM image

Selecting an image is one of the first and most important decisions you'll make when creating a VM. An image is a template that's used to create a VM. These templates include an OS and often other software, such as development tools or web-hosting environments.

Anything that a computer can have installed can be included in an image. You can create a VM from an image that's preconfigured to precisely the tasks you need, such as hosting a web app on the Apache HTTP Server.

 Tip

You can also create and upload custom disk images.

## Size your VM

Just as a physical machine has a certain amount of memory and CPU power, so too does a virtual machine. Azure offers a range of VMs of differing sizes at different price points. The size that you choose will determine the VM's processing power, memory, and maximum storage capacity.

 Warning

There are quota limits on each subscription that can impact VM creation. If you run into these quota limits you can [open an online customer support request](https://learn.microsoft.com/en-us/azure/azure-supportability/resource-manager-core-quotas-request) to increase your limits.

VM sizes are grouped into categories, starting with the B-series for basic testing and running up to the H-series for massive computing tasks. You should select the size of the VM based on the workload you want to perform. It's possible to change the size of a VM after it's been created, but the VM must be stopped first, so it's best to size it appropriately from the start if possible.

#### Here are some guidelines based on the scenario you are targeting

What are you doing?

Consider these sizes

**General use computing/web**: Testing and development, small to medium databases, or low to medium traffic web servers.

B, Dsv3, Dv3, DSv2, Dv2

**Heavy computational tasks**: Medium traffic web servers, network appliances, batch processes, and application servers.

Fsv2, Fs, F

**Large memory usage**: Relational database servers, medium to large caches, and in-memory analytics.

Esv3, Ev3, M, GS, G, DSv2, Dv2

**Data storage and processing**: Big data, SQL, and NoSQL databases that need high disk throughput and I/O.

Ls

**Heavy graphics rendering** or video editing, as well as model training and inferencing (ND) with deep learning.

NV, NC, NCv2, NCv3, ND

**High-performance computing (HPC)**: Your workloads need the fastest and most powerful CPU virtual machines with optional high-throughput network interfaces.

H

## Choose storage options

The next set of decisions revolves around storage. First, you can choose the disk technology. Options include a traditional platter-based hard disk drive (HDD) or a more modern solid-state drive (SSD). Just like the hardware you purchase, SSD storage costs more but provides better performance.

 Tip

There are two levels of SSD storage available: standard and premium. Choose Standard SSD disks if you have normal workloads but want better performance. Choose Premium SSD disks if you have I/O intensive workloads or mission-critical systems that need to process data very quickly.

### Map storage to disks

Azure uses virtual hard disks (VHDs) to represent physical disks for the VM. VHDs replicate the logical format and data of a disk drive but are stored as page blobs in an Azure Storage account. You can choose on a per disk basis what type of storage it should use (SSD or HDD). This allows you to control the performance of each disk, likely based on the I/O you plan to perform on it.

By default, two virtual hard disks (VHDs) will be created for your Linux VM:

1.  The **operating system disk**: This is your primary drive, and it has a maximum capacity of 2048 GB. It will be labeled as `/dev/sda` by default.
    
2.  A **temporary disk**: This provides temporary storage for the OS or any apps. On Linux virtual machines, the disk is `/dev/sdb` and is formatted and mounted to `/mnt` by the Azure Linux Agent. It's sized based on the VM size, and is used to store the swap file.
    

 Warning

The temporary disk is not persistent. You should only write data to this disk that is not critical to the system.

#### What about data?

You can store data on the primary drive along with the OS, but a better approach is to create dedicated _data disks_. You can create and attach additional disks to the VM. Each disk can hold up to 32,767 gibibytes (GiB) of data, with the maximum amount of storage determined by the VM size you select.

 Note

Azure virtual disk sizes are measured in Gibibytes (GiB), which are not the same as Gigabytes (GB); one GiB is approximately 1.074 GB. Therefore, to obtain an approximate equivalent of your virtual disk size in GB, multiply the size in GiB by 1.074, and that will return a size in GB that is relatively close. For example, 32,767 GiB would be approximately 35,183 GB.

An interesting capability is to create a VHD image from a real disk. This allows you to easily migrate _existing_ information from an on-premises computer to the cloud.

### Unmanaged vs. managed disks

The final storage choice you'll make is whether to use **unmanaged** or **managed** disks.

With unmanaged disks, you're responsible for the storage accounts that are used to hold the VHDs that correspond to your VM disks. You pay the storage account rates for the amount of space you use. A single storage account has a fixed rate limit of 20,000 I/O operations/sec. This means that a single storage account is capable of supporting 40 standard virtual hard disks at full throttle. If you need to scale out, then you need more than one storage account, which can get complicated.

Managed disks are the newer and recommended disk storage model. They elegantly solve this complexity by putting the burden of managing the storage accounts onto Azure. You'll specify the disk type (Premium or Standard) and the size of the disk, and Azure creates and manages both the disk _and_ the storage it uses. You don't have to worry about storage account limits, which makes them easier to scale out. They also offer several other benefits:

-   **Increased reliability**: Azure ensures that VHDs associated with high-reliability VMs will be placed in different parts of Azure Storage to provide similar levels of resilience.
-   **Better security**: Managed disks are real, managed resources in the resource group. This means they can use role-based access control to restrict who can work with the VHD data.
-   **Snapshot support**: You can use snapshots to create a read-only copy of a VHD. We recommend that you shut down the VM to clear out any processes that are in progress. Creating the snapshot only takes a few seconds. Once it's done, you can power on the VM and use the snapshot to create a duplicate VM to troubleshoot a production issue or roll back the VM to the point in time that you took the snapshot.
-   **Backup support**: Managed disks can be automatically backed up to different regions for disaster recovery with Azure Backup without affecting the VM's service.

## Network communication

Virtual machines communicate with external resources using a virtual network (VNet). The VNet represents a private network in a single region on which your resources communicate. A virtual network is just like the networks you manage on-premises. You can divide them up with subnets to isolate resources, connect them to other networks (including your on-premises networks), and apply traffic rules to govern inbound and outbound connections.

### Plan your network

When you create a new VM, you'll have the option of creating a new virtual network or using an existing VNet in your region.

Having Azure create the network together with the VM is simple, but it's likely not ideal for most scenarios. It's better to plan your network requirements _up front_ for all the components in your architecture and create the VNet structure separately. Then, create the VMs and place them into the already-created VNets. We'll look more at virtual networks later in this module.

Before we create a virtual machine, we need to decide how we'd like to administer the VM. Let's look at our options.

# Exercise - Decide an authentication method for SSH

Completed100 XP

-   10 minutes

This module requires a sandbox to complete. You have used 1 of 10 sandboxes for today. More sandboxes will be available tomorrow.

Activate sandbox

Before we can create a Linux virtual machine in Azure, we'll need to think about remote access. We want to be able to sign in to our Linux web server to configure the software and perform maintenance. The default approach to administering Linux VMs hosted in Azure is SSH.

## What is SSH?

Secure Shell (SSH) is an encrypted connection protocol that allows secure sign-ins over unsecured connections. SSH allows you to connect to a terminal shell from a remote location using a network connection.

There are two approaches we can use to authenticate an SSH connection: **username and password**, or an **SSH key pair**.

Although SSH provides an encrypted connection, using passwords with SSH connections leaves the VM vulnerable to brute-force attacks of passwords. A more secure and preferred method of connecting to a Linux VM with SSH is a public-private key pair, also known as SSH keys.

With an SSH key pair, you can sign in to Linux-based Azure virtual machines without a password. This is a more secure approach if you only plan to sign in to the VM from a few computers. If you need to be able to access the Linux VM from a variety of locations, a username and password combination might be a better approach. There are two parts to an SSH key pair: a public key and a private key.

-   The public key is placed on your Linux VM or any other service that you wish to use with public-key cryptography. This can be shared with anyone.
    
-   The **private key** is what you present to verify your identity to your Linux VM when you make an SSH connection. Consider this confidential information and protect it like you would a password or any other private data.
    

You can use the same single public-private key pair to access multiple Azure VMs and services.

## Create the SSH key pair

On Windows 10, Windows 11, Linux, and macOS, you can use the built-in `ssh-keygen` command to generate the SSH public and private key files.

Windows 10 includes an SSH client with the **Fall Creators Update**. Windows 11 includes an SSH client by default. Earlier versions of Windows require additional software to use SSH; [check the documentation for full details](https://learn.microsoft.com/en-us/azure/virtual-machines/linux/ssh-from-windows). Alternatively, you can install the Linux subsystem for Windows and get the same functionality.

We'll use Azure Cloud Shell, which stores the generated keys in Azure in your private storage account. You can also type these commands directly into your local shell if you prefer. You'll need to adjust the instructions throughout this module to reflect a local session if you take this approach.

Here's the minimum command necessary to generate the key pair for an Azure VM. This creates an SSH protocol 2 (SSH-2) RSA public-private key pair. The minimum length is 2048, but for the sake of this learning module, we'll use 4096.

1.  Run the following command in Cloud Shell.
    
    BashCopy
    
    ```
    ssh-keygen -m PEM -t rsa -b 4096
    ```
    
2.  Press Enter to accept the default location. The command creates two files: `id_rsa` and `id_rsa.pub` in the `~/.ssh` directory. The files are overwritten if they exist.
    
3.  Enter a passphrase that you'll remember. You'll need this passphrase when you use the SSH key to access the VM.
    

There are various options you can use to provide the file name or a passphrase to avoid the prompts.

### Private key passphrase

You can provide a passphrase while generating your private key. This is a password you must enter when you use the key. This passphrase is used to access the private SSH key file and isn't the user account password.

When you add a passphrase to your SSH key, it encrypts the private key using 128-bit AES so that the private key is useless without the passphrase to decrypt it.

We strongly recommended that you add a passphrase. If an attacker stole your private key and that key didn't have a passphrase, they would be able to use that private key to log in to any servers that have the corresponding public key. If a passphrase protects a private key, that attacker can't use it. This provides an additional layer of security for your infrastructure on Azure.

## Use the SSH key pair with an Azure Linux VM

After you have the key pair generated, you can use it with a Linux VM in Azure. You can supply the public key during the VM creation, or add it after the VM has been created.

You can view the contents of the file in Cloud Shell by running the following command.

BashCopy

```
cat ~/.ssh/id_rsa.pub
```

It will look something like the following output:

OutputCopy

```
ssh-rsa XXXXXXXXXXc2EAAAADAXABAAABAXC5Am7+fGZ+5zXBGgXS6GUvmsXCLGc7tX7/rViXk3+eShZzaXnt75gUmT1I2f75zFn2hlAIDGKWf4g12KWcZxy81TniUOTjUsVlwPymXUXxESL/UfJKfbdstBhTOdy5EG9rYWA0K43SJmwPhH28BpoLfXXXXXGX/ilsXXXXXKgRLiJ2W19MzXHp8z3Lxw7r9wx3HaVlP4XiFv9U4hGcp8RMI1MP1nNesFlOBpG4pV2bJRBTXNXeY4l6F8WZ3C4kuf8XxOo08mXaTpvZ3T1841altmNTZCcPkXuMrBjYSJbA8npoXAXNwiivyoe3X2KMXXXXXdXXXXXXXXXXCXXXXX/ azureuser@myserver
```

Copy this value so you can use it in the next exercise.

### Use the SSH key when creating a Linux VM

To apply the SSH key while creating a new Linux VM, copy the contents of the public key and supply it to the Azure portal, _or_ supply the public key file to the Azure CLI or Azure PowerShell command. We'll use this approach when we create our Linux VM.

### Add the SSH key to an existing Linux VM

If you've already created a VM, you can install the public key onto your Linux VM with the `ssh-copy-id` command. After the key has been authorized for SSH, it grants access to the server without a password, though you'll still be prompted for the passphrase on the key if you set one.

For example, if we had a Linux VM named _myserver_ with a user _azureuser_, we could run the following command to install the public key file, and authorize the user with the key.

BashCopy

```
ssh-copy-id -i ~/.ssh/id_rsa.pub azureuser@myserver
```

Now that we have our public key, let's switch to the Azure portal and create a Linux VM.


# Exercise - Create a Linux virtual machine with the Azure portal

Completed100 XP

-   20 minutes

This module requires a sandbox to complete. You have used 1 of 10 sandboxes for today. More sandboxes will be available tomorrow.

Activate sandbox

Recall that our goal is to move an existing Linux server running Apache to Azure. We'll start by creating an Ubuntu Linux server.

## Create a new Linux virtual machine

We can create Linux VMs with the Azure portal, the Azure CLI, or Azure PowerShell. The easiest approach when you're starting with Azure is to use the portal, because it walks you through the required information and provides hints and helpful messages during the creation.

1.  Sign in to the [Azure portal](https://portal.azure.com/learn.docs.microsoft.com) using the same account you used to activate the sandbox.
    
2.  On the Azure portal menu or from the **Home** page, under **Azure services**, select **Virtual machines**. Alternatively, you can enter _Virtual machines_ in the top search box, and press Enter. The **Virtual machines** pane appears.
    
3.  In the top menu bar, select **Create > Azure virtual machine**. The **Create a virtual machine** pane appears.
    

## Configure the VM settings, add data disks for the VM, and configure the network

The VM creation experience in the portal is presented in a wizard format to walk you through all the configuration areas for the VM. Selecting **Next** takes you to the next configurable tab. However, you can move between the tabs at will by selecting them in the sub menu.

[![Screenshot of the Azure portal showing Create a virtual machine pane for an Ubuntu Server machine.](https://learn.microsoft.com/en-us/training/modules/create-linux-virtual-machine-in-azure/media/3-azure-portal-create-vm.png)](https://learn.microsoft.com/en-us/training/modules/create-linux-virtual-machine-in-azure/media/3-azure-portal-create-vm.png#lightbox#lightbox)

After you complete all the required options (identified with red asterisks), you can skip the remainder of the wizard experience, and start creating the VM by selecting **Review + create** at the bottom of the wizard.

Remember that these instructions use the sandbox. If you're using another Azure portal account, you may need to adapt some details accordingly.

1.  On the **Basics** tab, enter the following values for each setting.
    
    Setting
    
    Value
    
    **Project details**
    
    Subscription
    
    Concierge Subscription (the sandbox subscription should be selected by default).
    
    Resource group
    
    Select **[sandbox resource group name]**.
    
    **Instance details**
    
    Virtual machine name
    
    Enter a name for your web server VM, such as **test-web-eus-vm1**. This indicates the environment (**test**), the role (**web**), location (**East US**), service (**vm**), and instance number (**1**). It's considered best practice to standardize your resource names, so you can quickly identify their purpose. Linux VM names must be between 1 and 64 characters and be composed of numbers, letters, and dashes.
    
    Region
    
    Select a location close to you. See the information below this table for available regions.
    
    Availability options
    
    Select **No infrastructure redundancy required**. This option can be used to ensure the VM is highly available by grouping multiple VMs together as a set to deal with planned or unplanned maintenance events or outages. For this exercise, we won't need this service.
    
    Security type
    
    Select **Standard**.
    
    Image
    
    From the dropdown list, select **Ubuntu Server 18.04 LTS - Gen2**
    
    VM architecture
    
    Select **x64**.
    
    Size
    
    Standard D2s v3. This option gives you two vCPUs with 8 GB of RAM.
    
    **Administrator account**
    
    Authentication type
    
    SSH public key
    
    Username
    
    Enter a name you'll use to sign in with SSH. Make a note of it.
    
    SSH public key source
    
    Use existing public key
    
    Key pair name
    
    Paste the SSH key from your public key file you created in the previous unit. It should look similar to the example shown in unit 3 with no additional whitespace or line-feed characters.
    
    Leave the rest of the options on this tab as their defaults.
    
    The free sandbox allows you to create resources in a subset of the Azure global regions. Select a region from the following list when you create resources:
    
    -   West US 2
    -   South Central US
    -   Central US
    -   East US
    -   West Europe
    
    -   Southeast Asia
    -   Japan East
    -   Brazil South
    -   Australia Southeast
    -   Central India
    
2.  Select **Next: Disks** to open the **Disks** tab.
    
3.  On the **Disks** pane, enter the following values for each setting.
    
    Setting
    
    Value
    
    **Disk options**
    
    OS disk type
    
    Premium SSD
    
    Delete with VM
    
    Checked
    
    Enable encryption at host
    
    Unchecked
    
    Encryption type
    
    (Default) Encryption at-rest with a platform-managed key
    
    **Data disks**
    
    _Recall that we will get an OS disk (/dev/sda) and a temporary disk (/dev/sdb). Here, we'll add a data disk as well._
    
    Create and attach a new disk
    
    Select the link. The **Create a new disk** pane appears. Accept all the default settings. Notice that source type is where you could use a snapshot or Azure Blob Storage to create a VHD.
    
4.  Select **OK** to create the disk. The **Disks** pane reappears on the **Create a virtual machine** pane.
    
    A new disk appears in the first row.
    
    [![Screenshot of the Azure portal showing the newly created data disk line for the VM creation process.](https://learn.microsoft.com/en-us/training/modules/create-linux-virtual-machine-in-azure/media/3-new-disk.png)](https://learn.microsoft.com/en-us/training/modules/create-linux-virtual-machine-in-azure/media/3-new-disk.png#lightbox)
    
5.  Select **Next: Networking** to move to the **Networking** tab.
    
6.  On the **Networking** pane, accept all the default values for each setting.
    
    In a production environment where we already have other components, you'd want to use an _existing_ virtual network. That way, your VM can communicate with the other cloud services in your solution. If there wasn't one defined in this location yet, you could create it here and configure the:
    
    -   **Subnet**: The first subnet to subdivide the address space. It must fit within the defined address space. After the VNet is created, you could add additional subnets.
    -   **Public IP**: The overall IPv4 space available to this network.
    
    By default, Azure creates a virtual network, network interface, and public IP for your VM. It's not trivial to change the networking options after the VM has been created, so always double-check the network assignments on services you create in Azure. For this exercise, the defaults should work fine.
    
    The rest of the options in the wizard have reasonable defaults, and there's no need to change any of them. You can explore the other tabs if you like. The individual options have an `(i)` icon next to them that will show a help tip to explain the option. This is a great way to learn about the various options you can use to configure the VM.
    
7.  Finish configuring the VM and creating the image by selecting **Review + create**.
    
8.  After the system validates your options and gives you details about the VM being created, select **Create** to create and deploy the VM. The Azure dashboard will show the VM that's being deployed. This may take several minutes.
    

While it's deploying, let's consider what we can do with this VM.

# Azure virtual machines IP addresses and SSH options

Completed100 XP

-   5 minutes

You've created a Linux VM in Azure. The next thing you’ll do is configure it for the tasks we want to move to Azure.

Unless you’ve set up a site-to-site VPN to Azure, your Azure VMs won’t be accessible from your local network. If you’re just getting started with Azure, it’s unlikely that you have a working site-to-site VPN. So how can you connect to the virtual machine?

## Azure VM IP addresses

As we saw a moment ago, Azure VMs communicate on a virtual network. They can also have an optional public IP address assigned to them. With a public IP, we can interact with the VM over the Internet. Alternatively, we can set up a virtual private network (VPN) that connects our on-premises network to Azure, letting us securely connect to the VM without exposing a public IP. This approach is covered in another module and is fully documented if you're interested in exploring that option.

Public IP addresses in Azure are dynamically allocated by default. That means the IP address can change over time; for VMs, the IP address assignment happens when the VM is restarted. You can pay more to assign static addresses if you want to connect directly to an IP address and need to ensure that the IP address won't change.

Due to these restrictions and the alternatives previously described, we'll use the public IP address of the VM in this module.

## Connect to the VM with SSH

To connect to the VM via SSH, you need the following items:

-   Public IP address of the VM
-   Username of the local account on the VM
-   Public key configured in that account
-   Access to the corresponding private key
-   Port 22 open on the VM

Previously, you generated an SSH key pair, and added the public key to the VM configuration, and ensured that port 22 was open.

In the next unit, you'll use this information to open a secure terminal on the VM using SSH.

After the terminal is open, you have access to all of the standard Linux command-line tools.

Next, let's connect to the VM using SSH.

# Exercise - Connect to a Linux virtual machine with SSH

Completed100 XP

-   15 minutes

This module requires a sandbox to complete. You have used 1 of 10 sandboxes for today. More sandboxes will be available tomorrow.

Activate sandbox

Let's connect to our Linux VM with SSH, and configure Apache, so we have a running web server.

### Get the public IP address of the VM

1.  In the [Azure portal](https://portal.azure.com/learn.docs.microsoft.com) from the previous exercise, select **Go to resource**. The **Overview** pane for the virtual machine that you just created appears. Alternatively, you can find the VM under **All Resources** if you need to open it. The overview pane allows you to:
    
    -   See if the VM is running.
    -   Stop or restart the VM.
    -   Get the public IP address of the VM.
    -   See the activity of the CPU, disk, and network.
2.  Select **Connect** > **SSH** at the top of the pane.
    
3.  Under step 4, copy the command to the clipboard.
    
    ![Screenshot of the Azure portal showing the Connect to a virtual machine pane configured to connect via SSH to the newly created Linux VM.](https://learn.microsoft.com/en-us/training/modules/create-linux-virtual-machine-in-azure/media/5-connect-ssh.png)
    
4.  We used the default SSH private key file path when we created the SSH key pair. We don't need to specify the private key path in the command by using the flag `-i` with the private key path. If you entered a different path when you created the SSH key pair, you'd add that path to the command.
    

## Connect with SSH

1.  Paste the command from your clipboard into Azure Cloud Shell. Delete the `-i` flag and the private key path placeholder, and run the command. It should look something like the following sample with a different IP address and username.
    
    BashCopy
    
    ```
    ssh azureuser@13.68.150.164
    ```
    
2.  The first time we connect, SSH will ask us about authenticating against an unknown host. SSH is informing you that you've never connected to this server before. If that's true, it's perfectly normal, and you can respond with **yes** to save the fingerprint of the server in the known host file.
    
    OutputCopy
    
    ```
    The authenticity of host '137.117.101.249 (137.117.101.249)' can't be established.
    ECDSA key fingerprint is SHA256:w1h08h4ie1iMq7ibIVSQM/PhcXFV7O7EEhjEqhPYMWY.
    Are you sure you want to continue connecting (yes/no)? yes
    Warning: Permanently added '137.117.101.249' (ECDSA) to the list of known hosts.
    ```
    
3.  Enter the passphrase you used when you created the SSH key pair.
    
4.  In the shell command prompt for Linux, try executing a few Linux commands:
    
    -   `ls -la /`: Shows the root of the disk
    -   `ps -l`: Shows all the running processes
    -   `dmesg`: Lists all the kernel messages
    -   `lsblk`: Lists all the block devices - here you'll see your drives
    
    The more interesting thing to observe in the list of drives is what is _missing_. Notice that our **Data** drive (`sdc`) is present but not mounted into the file system. Azure added a VHD, but didn't initialize it.
    

## Initialize data disks

Any additional drives you create from scratch need to be initialized and formatted. The process for initializing is identical to a physical disk.

1.  First, identify the disk that we just created. You could also use `dmesg | grep SCSI`, which will list all the messages from the kernel for SCSI devices.
    
2.  After you know the drive (`sdc`) you need to initialize, you can use `fdisk` to do that. You'll need to run the command with `sudo`, and supply the disk you want to partition. We can use the following command to create a new primary partition.
    
    BashCopy
    
    ```
    (echo n; echo p; echo 1; echo ; echo ; echo w) | sudo fdisk /dev/sdc
    ```
    
3.  Next, we need to write a file system to the partition with the `mkfs` command.
    
    BashCopy
    
    ```
    sudo mkfs -t ext4 /dev/sdc1
    ```
    
4.  Finally, we need to mount the drive to the file system. Let's assume we'll have a `data` folder. Let's create the mount point folder and mount the drive.
    
    BashCopy
    
    ```
    sudo mkdir /data && sudo mount /dev/sdc1 /data
    ```
    

We initialized the disk, and mounted it. If you want more details on this process, see the **[Add and size disks in Azure virtual machines](https://learn.microsoft.com/en-us/training/modules/add-and-size-disks-in-azure-virtual-machines/)** module. This task is covered in more detail there.

## Install software onto the VM

As you can see, SSH allows you to work with the Linux VM just like a local computer. You can administer this VM as you would any other Linux computer: installing software, configuring roles, adjusting features, and other everyday tasks. Let's focus on installing software for a moment.

You can also install software from the internet when you're connected to the VM via SSH. Azure machines are, by default, internet connected. You can use standard commands to install popular software packages directly from standard repositories. Let's use this approach to install Apache.

### Install the Apache web server

Apache is available within Ubuntu's default software repositories, so we'll install it using conventional package management tools:

1.  Start by updating the local package index to reflect the latest upstream changes:
    
    BashCopy
    
    ```
    sudo apt-get update
    ```
    
2.  Next, install Apache:
    
    BashCopy
    
    ```
    sudo apt-get install apache2 -y
    ```
    
3.  It should start automatically. We can check the status using `systemctl`:
    
    BashCopy
    
    ```
    sudo systemctl status apache2 --no-pager
    ```
    
    The `systemctl` command returns something like the following output:
    
    OutputCopy
    
    ```
    apache2.service - The Apache HTTP Server
       Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
      Drop-In: /lib/systemd/system/apache2.service.d
               └─apache2-systemd.conf
       Active: active (running) since Mon 2018-09-03 21:00:03 UTC; 1min 34s ago
     Main PID: 11156 (apache2)
        Tasks: 55 (limit: 4915)
       CGroup: /system.slice/apache2.service
               ├─11156 /usr/sbin/apache2 -k start
               ├─11158 /usr/sbin/apache2 -k start
               └─11159 /usr/sbin/apache2 -k start
    
    test-web-eus-vm1 systemd[1]: Starting The Apache HTTP Server...
    test-web-eus-vm1 apachectl[11129]: AH00558: apache2: Could not reliably determine the server's fully qua
    test-web-eus-vm1 systemd[1]: Started The Apache HTTP Server.
    ```
    
4.  Finally, we can try retrieving the default page through the public IP address. However, even though the web server is running on the VM, you won't get a valid connection or response. Do you know why?
    

We need to perform one more step to be able to interact with the web server. Our virtual network is blocking the inbound request. We can change that through configuration. Let's look at allowing the inbound request next.

# Network and security settings

Completed100 XP

-   10 minutes

Making adjustments to server configuration is commonly performed with equipment in your on-premises environment. In this sense, you can consider Azure VMs to be an extension of that environment. You can alter configuration, manage networks, open or block traffic, and more through the Azure portal, the Azure CLI, or Azure PowerShell tools.

We've got our server running, and Apache is installed and serving up pages. Our security team mandates that we lock down all our servers, and we've not done anything to this VM yet. We didn't do anything, and it let Apache listen on port 80. Let's explore the Azure network configuration to see how to use the built-in security support to harden our server.

## Open ports in Azure VMs

By default, new VMs are locked down.

Apps can make outgoing requests, but the only inbound traffic allowed is from the virtual network (for example, other resources on the same local network) and from Azure Load Balancer (probe checks).

There are two steps for adjusting the configuration to support different protocols on the network. When you create a new VM, you have an opportunity to open a few common ports (RDP, HTTP, HTTPS, and SSH). However, if you require other changes to the firewall, you'll need to adjust them manually.

The process involves two steps:

-   Create a network security group.
-   Create an inbound rule allowing traffic on the ports you need.

### What is a network security group?

Virtual networks (VNets) are the foundation of the Azure networking model, and provide isolation and protection. Network security groups (NSGs) are the primary tool you'll use to enforce and control network traffic rules at the networking level. NSGs are an optional security layer that provides a software firewall by filtering inbound and outbound traffic on the VNet.

Security groups can be associated to a network interface (for per host rules), a subnet in the virtual network (to apply to multiple resources), or both levels.

#### Security group rules

NSGs use _rules_ to allow or deny traffic moving through the network. Each rule identifies the source and destination address (or range), protocol, port (or range), direction (inbound or outbound), a numeric priority, and whether to allow or deny the traffic that matches the rule.

![An illustration showing the architecture of network security groups in two different subnets. In one subnet, there are two virtual machines, each with their own network interface rules. The subnet itself has a set of rules that applies to both the virtual machines.](https://learn.microsoft.com/en-us/training/modules/create-linux-virtual-machine-in-azure/media/7-nsg-rules.png)

Each security group has a set of default security rules to apply the default network rules previously described. You can't modify these default rules, but you can override them.

#### How Azure uses network rules

For inbound traffic, Azure processes the security group associated to the subnet, then the security group applied to the network interface. Outbound traffic is handled in the opposite order (the network interface first, followed by the subnet).

 Warning

Keep in mind that security groups are optional at both levels. If no security group is applied, then Azure **allows all traffic**. If the VM has a public IP, this could be a serious risk, particularly if the OS doesn't provide a built-in firewall.

The rules are evaluated in _priority order_, starting with the **lowest priority** rule. Deny rules always **stop** the evaluation. For example, if a network interface rule blocks an outbound request, any rules applied to the subnet won't be checked. For traffic to be allowed through the security group, it must pass through _all_ applied groups.

The last rule is always a **Deny All** rule. This is a default rule added to every security group for both inbound and outbound traffic, with a priority of 65500. That means to have traffic pass through the security group, _you must have an allow rule_, or the final default rule will block it.

 Note

SMTP (port 25) is a special case. Depending on your subscription level and when your account was created, outbound SMTP traffic may be blocked. You can request to remove this restriction with business justification.

## Create network security groups

Security groups are managed resources like most everything in Azure. You can create them in the Azure portal or through command-line scripting tools. The challenge is in defining the rules. Let's look at defining a new rule to allow HTTP access and block everything else.

# Exercise - Configure network settings

Completed100 XP

-   10 minutes

This module requires a sandbox to complete. You have used 1 of 10 sandboxes for today. More sandboxes will be available tomorrow.

Activate sandbox

When we created the VM, we selected the inbound port _SSH_ so we could connect to the VM. This created an NSG that's attached to the network interface of the VM. That NSG is blocking HTTP traffic. Let's update this NSG to allow inbound HTTP traffic on port 80.

## Update the NSG on the network interface

Port 80 is open on the NSG applied to the subnet. But port 80 is blocked by the NSG applied to the network interface. Let's fix that so we can connect to the website.

1.  Switch back to the **Overview** pane for the VM. You can find the VM under **All Resources**.
    
2.  In the left menu pane, under **Settings**, select **Networking**.
    
3.  You should have the NSG rules for the subnet in the top section, and the NSG rules for the network interface in the bottom section of the same tab. In the bottom section, for the NSG rules for the network interface, select **Add inbound port rule**.
    
    ![Screenshot that shows the "Add inbound port rule" button in the network security group > network interface section.](https://learn.microsoft.com/en-us/training/modules/create-linux-virtual-machine-in-azure/media/8-add-rule-network-interface.png)
    
    The **Add inbound security rule** pane appears.
    
4.  Enter the following values for our HTTP rule.
    
    Setting
    
    Value
    
    Service
    
    HTTP
    
    Priority
    
    310
    
    Name
    
    allow-http-traffic
    
    Description
    
    Allows http traffic
    
    ![Screenshot of that shows the basic form filled out.](https://learn.microsoft.com/en-us/training/modules/create-linux-virtual-machine-in-azure/media/8-inbound-rule-basic-form.png)
    
5.  Select **Add** to create the rule. The **Networking** pane for your VM reappears.
    

## Open the default webpage

To make an HTTP request, copy and paste the **NIC Public IP** address of the server into a browser, and press Enter. It should now work.

![Screenshot of a web browser showing the Apache default web page hosted at the IP of the new Linux VM.](https://learn.microsoft.com/en-us/training/modules/create-linux-virtual-machine-in-azure/media/8-apache-works.png)

## One more consideration

Always make sure to lock down ports used for administrative access. An even better approach is to create a VPN to link the virtual network to your private network, and only allow RDP or SSH requests from that address range. You can also change the port used by SSH to be something other than the default. Keep in mind that changing ports isn't sufficient to stop attacks. It simply makes it a little harder to discover.