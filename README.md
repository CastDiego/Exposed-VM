# Exposed-VM
An Exposed VM hosted on Azure. Using Sentinel to see the malicious attackers and logging results.
Azure Sentinel Monitoring
Creation, Configuration, and Reporting 
This project is to show the creation of a VM and have it exposed to the internet with no active firewall rules. The VM will then have log analytics connected to report to Azure Sentinel for reporting. Finally, Azure sentinel will report and show active attackers via IP, Country, and username tested. 
Creating VM
1.	Create a VM in a new Resource group. (Fig 1)
a.	The Resource group is named Honeypot
2.	Region in East US, and security is set to standard. Every other field can be left as default.
3.	Select Advance network to create a network security group (Fig 2)
4.	The NSG (network security group) should be set to allow all. 
a.	RDP open to all ips, set to 100 priority.
![image](https://user-images.githubusercontent.com/126493608/230472572-3aee3cd2-3eb2-461a-8415-4b7391035184.png)
Fig.1
![image](https://user-images.githubusercontent.com/126493608/230472614-90b8299e-0364-48b9-b482-a179b2027906.png)
Fig.2
Log into VM
1.	Use the public IP listed on the machine to log in (Fig 3)
2.	Use Incorrect user name to log in (example) Random_attacker
3.	Log incorrectly, open event viewer > security > and look for the event. The Radom_attacker is shown to log in. (Fig 4)
4.	Disable firewall (Fig 5)
5.	Download Powershell Script from Joshmadakor1. Sentinel-lab (github)
6.	Activate API key from ipgeolocation.io (Fig 6)
![image](https://user-images.githubusercontent.com/126493608/230472771-e2b640e9-64cf-4157-89fb-fcc31ded26bd.png)
Fig. 3
![image](https://user-images.githubusercontent.com/126493608/230472806-37c14cc2-117c-40c0-b94a-c6ba1a07ad65.png)
Fig. 4
![image](https://user-images.githubusercontent.com/126493608/230472845-3e289639-fdae-491c-9deb-6bc556d03cc1.png)
Fig.5
![image](https://user-images.githubusercontent.com/126493608/230472867-f3063813-1d0c-4460-b8dc-f87e9aa2aaac.png)
Fig 6
Create Log Analytics Workspace 
1.	In Azure, go to Log Analytics and create. (Fig 7)
2.	Connect the VM to the workspace
3.	Add a Custom log to the workspace (This will be the sample log that gets output from the Powershell script)
4.	Point the log to the file path on the VM 
5.	Extract Fields from the export log. (We are doing this to help train a classifier to pull specific data like longitudinal and latitudinal data. (Fig 8)
![image](https://user-images.githubusercontent.com/126493608/230472952-07a09acb-ce0f-4967-bac4-e7610f95241d.png)
Fig. 7
![image](https://user-images.githubusercontent.com/126493608/230473004-48aa697f-551e-416a-b565-10f6895b98c7.png)
Fig 8.1
![image](https://user-images.githubusercontent.com/126493608/230473037-a70cb4fd-5213-4dcb-b587-399c6b70b196.png)
Fig 8.2
![image](https://user-images.githubusercontent.com/126493608/230473061-14cf8f3f-0df5-4120-8b1e-19907578335f.png)
Fig 8.3
Create & Reporting Microsoft Sentinel 
1.	In Sentinel create a new workspace and connect the Log Analytics log.
2.	Create a Workbook 
a.	Give it a name and create the query. (Fig 9)
3.	Having the logs represented on a map, and checking after a few hours.
a.	We should have a few logs that show up.  (Fig 10)
4.	The Machine will have the logs show people who and what username/ Ip and location they are from.
![image](https://user-images.githubusercontent.com/126493608/230473100-c6481120-1aa5-415c-b882-1445d9a0210e.png)
Fig. 10
![image](https://user-images.githubusercontent.com/126493608/230473148-1799be00-f993-47b9-b39d-a4a3fa4bd965.png)
Fig. 11
Topology
![image](https://user-images.githubusercontent.com/126493608/230473411-5e9d7fc8-a455-43ce-9501-6fb683fa610b.png)

