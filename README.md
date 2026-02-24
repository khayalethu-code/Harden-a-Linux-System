# PROJECTNAME

## Objective
  * Use a security auditing tool to discover system vulnerabilities.

* Implement recommended solutions to harden the system.
  
### Skills Learned

* Vulnerability Management: The ability to use automated tools to discover hidden system flaws.

* Repository Management: Knowing how to securely add and verify third-party software sources using GPG keys.

* System Patching: Mastery of apt-get commands to resolve high-impact security warnings.

### Tools Used

* PC with the CSE-LABVM installed in VirtualBox

## How It helps an organization?

In a corporate environment, this process isn't just a lab exercise, it’s a survival strategy.

* Risk Mitigation: Organizations use these audits to identify "low-hanging fruit" for attackers, such as unpatched browsers (like Firefox) or open ports, before a breach occurs.

* Compliance: Many industries require regular security audits. Using tools like Lynis helps an organization prove they are following "Best Practices" and "Hardening Standards".

* Operational Integrity: Updating a system to its latest version prevents performance issues and ensures that the software is stable and supported by the vendor.

* Reduced Downtime: Proactive hardening is always cheaper than reactive disaster recovery. A single patched vulnerability could save an organization from a catastrophic ransomware attack.

 ## Steps

## Part 1:

## Installed and Update Lynis on the workstation. ##

Step 1: Determined the installed Lynis version by launching the CSE-LABVM.

* Double-clicked the Terminal icon to open a terminal.

* To determine the latest version provided by CISOfy, I entered  the following command at the terminal: cisco@labvm:~$ sudo apt-cache policy lynis
  
<img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/4404c621-d12d-44c2-a9d1-c48992051e9f" />

* Here Lynis was not installed so to install it , I copied and pasted the following command into a terminal to import the key from the CISOfy keyserver. This key is required to verify the integrity of the  download when I download lynis: cisco@labvm:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 013baa07180c50a7101097ef9de922f1c2fde6c4

*  I Performed  an update after adding a new repository using the command : sudo apt-get update.
  
  <img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/3aba0100-c295-4a5f-a9b7-db4f6efbed7c" />
  
  * If I try to check if Lynis is installed using the : sudo apt-cache policy lynis commmand, still its not installed
    
    <img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/ba09a520-94d3-4fab-a82c-7b979bafbbf9" />
    
    * To fix this issue , I used the command : sudo apt install Lynis
      <img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/bdd8caa3-7a18-4484-a624-a95c2bd1e54c" />

      * I then performed an upgrade after the installation to ensure that the installed Lynis is latest version, by enetering : sudo apt-get upgrade
        
        <img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/dba008f7-5dfe-4d82-ae1f-74823a4d61f9" />
        
      * as you can see Lynis is now installed after entering the :  sudo apt-cache policy lynis commmand

        <img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/279ec244-e68e-406a-b91d-3d3330478cd3" />

## Part 3: ##

To run the Lynis tool, I entered  the : sudo lynis --auditor cisco command

<img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/fc39a942-81e4-482a-947f-07030fa08660" />
<img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/907531af-1622-46f1-a4e4-10e02a48657e" />
<img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/74a13bcd-a10b-4255-95d6-61baf96736ae" />
<img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/3444eff1-aab6-48c4-a438-73b02ddc5e08" />

* Here are the Lynis Hardening Results and suggestions
  
* <img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/c627b1e2-f8c6-4b6c-bc74-4a333982ab2a" />
<img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/761b3436-4573-4128-aca1-cd3a06694796" />
<img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/29dab712-e0e0-4735-9d3b-7466fb1e8829" />
<img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/7c53a948-45a6-411d-aa17-a77576646fdb" />
<img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/9bb9bfe9-6813-4063-9ccb-46f4da558ef3" />
<img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/24c5ab87-dbce-410f-a9a7-3ca1698ada7d" />
<img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/a555e5d4-feac-4a29-bcf5-dc932132dd15" />

* Here is the Lynis follow-up and details
  
* <img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/05d15ddd-2860-429d-ae58-3a6270e20e9d" />
<img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/60f2a85d-3e63-4589-93e6-cd6126ff3364" />
<img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/834e0017-797a-4d9c-bbda-4a3e2e12c034" />

* I've found this two warnings
  
  <img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/f7ec0820-3270-41b9-9514-50fdd4a90626" />
  
  ## Now I have to fix all the warnings:
  * To know exactly which packages are flagged before I start updating blindly, I had to run this command to extract the specific package names from the Lynis log: sudo grep "PKGS-7392" /var/log/lynis.log
  * 
    <img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/9803c216-1cab-4294-b89d-ae0442e2ae33" />
    
    * This output, it means Lynis is seeing a mismatch between the installed versions and the security manifests in the Ubuntu repositories.
      
      * To identify the Vulnerable Packages and since the Lynis log was generic,I used the native package manager to list exactly what is flagged by running : apt list --upgradable | grep -i security
      * 
        <img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/2bbc54fc-3378-44e3-91ae-ba83c9b93469" />
        
        * To perform a Dry Run : sudo apt upgrade --simulate
        * 
          <img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/39a7516b-3711-44a4-a637-eb8f00eb2172" />
          
         * To apply the security fixes, I used dist-upgrade. Unlike a standard upgrade, this ensures that dependencies are handled correctly, which is often why Lynis flags packages as "vulnerable" when they are actually just "held back.": sudo apt update && sudo apt dist-upgrade -y.
         * This command took more than 30 minutes to complete
           
  <img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/54c7f481-d9c5-40f9-8d37-792ca1422a0e" />
<img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/b42ef6f7-5779-44d1-876d-f0220c2d4849" />
<img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/f84b1b46-755d-4c69-88d4-ecbcc181a70d" />

* On the final Verification , I had to prove to Lynis that I’ve done my jobs. I had to run the audit again, by using a "quick check" to save time: sudo lynis audit system --tests-from-group debian

<img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/45e9000c-54e9-40ff-8426-4b83673be95c" />

* As you can see after the audit, there are no warnings which proves I hardened The system successfully
  
<img width="1920" height="892" alt="image" src="https://github.com/user-attachments/assets/2676c2a9-ff83-4bd7-b6d9-21d31ed536a8" />















 


