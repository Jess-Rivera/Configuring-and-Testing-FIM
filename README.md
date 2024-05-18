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


- Wazuh SIEM
- Powershell
- Linux CLI

## Steps
