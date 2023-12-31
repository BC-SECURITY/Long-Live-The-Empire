# Exercise 2: Agent Deployment Basics
This exercise guides you through the basics of agent deployment, including the creation of a listener on Starkiller, generating a stager for command execution, and finally, deploying the agent on a workstation. These steps provide practical experience in effectively deploying and managing agents within a network, and will be using the Kali Linux machine in Immersive Labs.


## Deploy a Listener
In this section, we'll be setting up a listener. A listener operates as a server-side entity that awaits incoming connections from agents on specific network ports. It's responsible for managing the communication with deployed agents, thereby ensuring successful data transfer and command execution. Let's dive into creating our first listener!

1. Log in to Starkiller at `http://localhost:1337/index.html`. Username is `empireadmin` and password is `password123`
2. Click on Listeners. (It's the headphones icon)
3. Then click the orange create button in the top right 
4. Select `http` from the dropdown
5. Set the `Port` to 80 and leave everything else to default 

<p align="center">
  <img src="https://github.com/BC-SECURITY/Empire/assets/20302208/a5dfcbd8-11b5-4f6f-ab35-b4610770581b"
</p>

6. click `submit`

## Generate a Stager
Next, we will explore the concept of stagers. A stager is a small piece of code or software that is used to stage the delivery of a payload to a target system. Its primary role is to establish an initial foothold on the target, which can then be used to further download and execute the full payload.

1. Click on Stagers (It's the suitcase icon)  
2. Then click Create and select a `multi_launcher` from the dropdown
3. Select the listener you created from the dropdown 
4. Leave the other fields as defaults 
5. Click `Submit` in the top right corner 

<p align="center">
  <img src="https://github.com/BC-SECURITY/Empire/assets/20302208/5fc291d5-76c6-451b-8a71-e877efa99313"
</p>

## Deploy the Agent
An agent is the operating code that is used as the implant on a target system. It maintains communication with Empire through the listener, allowing the attacker to control, monitor, and execute commands on the compromised system.

1. Login to Workstation 1 (10.10.0.45)
2. Turn off Real-Time Protections (if enabled)

<p align="center">
   <img width="770" alt="image" src="https://user-images.githubusercontent.com/20302208/154829916-27c4aac3-1a3b-44d6-83a1-957d570e18a9.png">
</p>

3. Open PowerShell.exe
4. Go back to Starkiller and click on the three dots under actions and select copy to clipboard

<p align="center">
   <img width="770" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/93e24fcf-bdaa-4e5d-a902-b6e93f3ebeae">
</p>

5. Paste the payload into PowerShell.exe on Workstation 1 and run it (if you are having issues cutting and pasting you can press `ctl+alt+shift` to open the guacamole to add the payload. Press it a second time to close the guacamole window. 

<p align="center">
   <img width="913" alt="252177318-d2c41ae5-bb57-4037-86e7-d423efb1191a" src="https://github.com/BC-SECURITY/Empire/assets/20302208/affa456f-a408-4e93-96f2-061d72cfe33b">
</p>

6. A successful agent callback will give a notification on the bottom left of the screen and display the new agent on the Agents tab.

<p align="center">
    <img width="782" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/9734c080-5ec3-4922-8fac-ebf53420cc4d">
</p>
