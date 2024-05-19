# Configuring and Testing FIM

## Objective

This lab practices two of three concepts in the CIA triad (Confidentiality, Integrity, Availability).

Availability was practiced by creating a RAID 1 configuration. This configuration duplicates all data across the drives in the RAID 1 configuration so that if one drive fails, the availability of the files are available on the remaining drives. The RAID 1 used in this practice was two VHDs created in Windows 11 and then a folder copied into it.

Integrity was practiced by setting up and monitoring the open-source SIEM Wazuh. The manager was installed on an Alma Linux machine, the agent was the Windows 11 machine. Once set up, a file was created in the target folder and then modified. Then a separate file was modified. The manager was checked to ensure the changes were captured.

### Skills Learned

- Basic understanding of SIEM agent set up on Manager and Client devices. 
- Deepened understanding of RAID set up and usage.
- Ability to add a target folder to a FIM. 

### Tools Used
<div>
    <img src="https://img.shields.io/badge/-Wazuh-001B49?&style=for-the-badge&logo=Wazuh&logoColor=white" />
    <img src="https://img.shields.io/badge/-Windows%2011-0078D6?&style=for-the-badge&logo=Windows&logoColor=white" />
    <img src="https://img.shields.io/badge/-PowerShell-5391FE?&style=for-the-badge&logo=PowerShell&logoColor=white" />
    <img src="https://img.shields.io/badge/-Alma%20Linux-082336?&style=for-the-badge&logo=AlmaLinux&logoColor=white" />
</div>


## Steps

#### Initial Raid Setup
I initially created 2 VHDs of 5GB each in Win11, then created the RAID 1 VOL using the 2 VHDs.
![Setting up RAID 1 Configuration utilizing VHDs in Win11](https://github.com/Jess-Rivera/Configuring-and-Testing-FIM/blob/main/FIM_raid_setup.PNG)

#### Wazuh
I moved to my Alma Linux machine and verified that Wazuh was running using the terminal.

![Verify Wazuh Running](https://github.com/Jess-Rivera/Configuring-and-Testing-FIM/blob/main/FIM_verify_wazuh_running.PNG)

Once verified, I signed into Wazuh and created an agent for the WIN11 machine.

![Adding Agent in Wazuh](https://github.com/Jess-Rivera/Configuring-and-Testing-FIM/blob/main/FIM_wazuh_add_agent.PNG)

At this point I ran into some technical issues with Wazuh not wanting to run properly on my virtual Win11. After several restarts and careful input I finally got Wazuh running as an Agent on my Win11 machine. 

![Wazuh Running on Win11](https://github.com/Jess-Rivera/Configuring-and-Testing-FIM/blob/main/FIM_wazuh_run_win11.PNG)

I then added the target directory to the agent configuration file and performed a few manipulations in the target folder.

![Adding Target Directory to Wazuh on WIN11](https://github.com/Jess-Rivera/Configuring-and-Testing-FIM/blob/main/FIM_adding_target_directory.PNG)

Finally, I went back to my Alma Linux machine and verified that the changes I performed were tracked. 

![FIM Check on Linux](https://github.com/Jess-Rivera/Configuring-and-Testing-FIM/blob/main/FIM_check_mod.PNG)

## Challenges and Solutions
I ran into a fairly frustrating problem of not being able to get Wazuh to run on my client VM WIN11 machine. After several restarts, I took my time and verified each letter for the command to install Wazuh on the WIN11 machine. I finally got it working. The lesson I learned here is that fast is slow. I need to take my time to type in the correct commands on the CLI, otherwise I will just not get the results I want. 

Another challenge, or perhaps its just the set up of my VMs, is that I was inpatient when checking the FIM and refreshed the page to verify my changes. I'm not sure if it updates automatically. I'll have to look into if it was my inpatience, the VM setup creating a lag, or perhaps it just needs to be refreshed. 

## Reflection and Learning
I really sped through initially because the steps seemed easy in my reading before doing the practice. I learned the hard way that I need to be slow and deliberate. This matches with my experience in the nuclear Navy, and I suppose that I didn't apply the same level of deliberation to this practice because in the back of my mind it wasn't as high stakes. Cybersecurity is high stakes. Even though this was practice in a safe environment, I need to treat all my practice as the real thing. Practice makes perfect.

I learned a lot through this practice. Getting hands on experience in SIEM, FIM, RAID was fantastic. Really moves the knowledge I have from my coursework, certification study, and reading into reality. I am excited to do another project, much more deliberate next time though.
