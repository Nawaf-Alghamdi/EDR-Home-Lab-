# EDR | Attack and Defense
# Project
This lab is dedicated to simulating a real Cyber Attack and endpoint detection and response. Utilizing Eric Capuano's guide online, I will be using virtual machines to simulate the threat & victim machines. The attack machine will utilize 'Sliver' as a C2 framework to attack a Windows endpoint machine, which will be running 'LimaCharlie' as an EDR solution.
# Setup
The first step to the lab is setting up both machines. The attack machine will run on Ubuntu Server, and the endpoint will be running Windows 11. In order for this lab to work smoothly Microsoft Defender should be turned off (along with other settings). I am also going to be installing Sliver on the Ubuntu machine as my primary attack tool, and setting up LimaCharlie on the Windows machine as an EDR solution. LimaCharlie will have a sensor linked to the windows machine, and will be importing sysmon logs.
![image](https://github.com/user-attachments/assets/273ede36-092b-4574-acd7-e9ca8c468a8e)
![image](https://github.com/user-attachments/assets/8cddfb80-5d07-40de-abc9-60d4c0957abb)
![image](https://github.com/user-attachments/assets/2d34205e-184d-4abf-8e62-0618bd92fa0c)
![image](https://github.com/user-attachments/assets/6e8ec2f1-ebdd-46e2-831a-e590ed68de9e)
# The Attacks, and the Defense
The first step is to generate our payload on Sliver, and implant the malware into the Windows host machine. Then we can create a command and control session after the malware is executed on the endpoint.
![image](https://github.com/user-attachments/assets/35e6cccd-2e67-41b7-85ae-1f324a078072)
![image](https://github.com/user-attachments/assets/da81e2ad-e961-4a3b-a9fb-f8d8c2f56666)
![image](https://github.com/user-attachments/assets/5ee57829-42cc-4c0c-b57b-0c93bb4bb1a1)






