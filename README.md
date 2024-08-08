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


Now that we have a live session between the two machines, the attack machine can begin peeking around, checking priveleges, getting host information, and checking what type of security the host has.
![image](https://github.com/user-attachments/assets/92a33626-a963-4723-8013-a8b4782c0615)
![image](https://github.com/user-attachments/assets/92925faf-516e-40a8-9fe9-28a4578aa0d8)


On the host machine we can look inside our LimaCharlie SIEM and see telemetry from the attacker. We can identify the payload thats running and see the IP its connected to.
![image](https://github.com/user-attachments/assets/a2782d94-176b-48d4-836e-6843b253ff1b)
![image](https://github.com/user-attachments/assets/e707584b-4e45-45ed-82ed-069675624db7)
![image](https://github.com/user-attachments/assets/5cb40538-e604-4141-9f2b-296c4844c746)


We can also use LimaCharlie to scan the hash of the payload through VirusTotal; however, it will be clean since we just created the payload ourselves.
![image](https://github.com/user-attachments/assets/701344a5-062d-4112-a1ae-8d6baf3cf3d2)
![image](https://github.com/user-attachments/assets/afa4f43c-70e9-4d54-afc5-934d4ed10c55)

Now on the attack machine we can simulate an attack to steal credentials by dumping the LSASS memory. In LimaCharlie we can check the sensors, observe the telemetry, and write rules to detect the sensitive process.
![image](https://github.com/user-attachments/assets/e24d9256-60f3-4db9-9923-01cb3d5c2f09)
![image](https://github.com/user-attachments/assets/3236904d-1f44-40e2-8536-0881a3b95b1d)



Now instead of simply detection, we can practice using LimaCharlie to write a rule that will detect and block the attacks coming from the Sliver server. On the Ubuntu machine we can simulate parts of a ransomware attack, by attempting to delete the volume shadow copies. In LimaCharlie we can view the telemetry and then write a rule that will block the attack entirely. After we create the rule in our SIEM, the Ubuntu machine will have no luck trying the same attack again.
![image](https://github.com/user-attachments/assets/6d3c0021-5bc6-4c8b-987c-82146e02a90a)
![image](https://github.com/user-attachments/assets/063a2bb0-c2f4-4cf3-b0f8-8bc3da530c61)
![image](https://github.com/user-attachments/assets/83ac82e9-80bc-4dd7-b803-b5629ff59b18)
![image](https://github.com/user-attachments/assets/c04d1810-5936-425d-95b7-7c167d8b33c0)
# Conclusion
This home lab project effectively demonstrates a simulated cyber attack and defense scenario using virtual machines and specific tools: Sliver as the C2 framework on an Ubuntu server, and LimaCharlie as the EDR solution on a Windows 11 endpoint. Following Eric Capuano's guide, we set up the environment, disabled default security measures, and conducted various attack simulations to test the effectiveness of LimaCharlie.


This exercise provided practical experience in both offensive and defensive cybersecurity measures, showcasing the importance of EDR solutions in detecting and responding to cyber threats. By simulating real-world attacks and defenses, we gained valuable insights into the dynamics of endpoint security and incident response.

















