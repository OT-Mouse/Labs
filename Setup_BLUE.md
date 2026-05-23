# Overview



Blue is a Windows 7 Ultimate machine that is deliberately vulnerable machine 
(credit goes to TryHackMe)

-The goal is to mainly get comfortable with Metasploit and try to compromise the machine.

## Steps to run the Blue .VMDK file in a Proxmox environment:


1. First you'll want to copy the file as path (if you're using windows) and SCP the file over to a user with root access using the following command

- scp <C:\path\to\Blue> username@Proxmox-IP-address:/var/lib/vz/images/


2. After the .VMDK has been transferred over to your server you'll go over to the console and convert the file format over to .q2cow using the below command


- qemu-img convert -p -f vmdk -O qcow2 /var/lib/vz/images/machine-disk001.vmdk /var/lib/vz/images/machine.qcow2

- The "-P" flag is going to show progress for the people who like to see that.


3. Create the VM in the Proxmox UI unless and note the VM ID that get's assigned
- at this point you'll also delete the default disk during configuration as well

4. Back in the shell you'll run the below command to import the disk to the VM that was just created

- qm importdisk <VMID> /var/lib/vz/images/machine.qcow2 local

**Keep in mind that sometimes the local storage needs to be adjusted to actually use the entire disk available otherwise you'll run low on local storage really fast**

5. After you've imported the disk you'll want to navigate over to the VM you created click "Hardware" --> "Unused disk 0" --> "Edit"

- Set it to IDE
- Then hit Add

6. After all of that you'll go over to the options tab within the proxmox UI and click:           "Boot Order" --> "Edit" --> make the imported disk the first boot option



### Other notes about this setup:

-Windows VMs use E1000 Network adapter and sometimes you need to get the driver ISO to compensate for when the image doesn't have it and you'll have to mount that during intial setup as well. For this part you'll need to power off the VM to mount the drivers ISO


### This VM can be ran with the following hardware allocation

- 2GB RAM
- 1 socket 2 cores
- BIOS (Default SEA BIOS)
