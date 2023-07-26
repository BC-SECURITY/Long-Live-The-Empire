# Agent Chaining
In this exercise, we will explore the process of agent chaining using Empire. The key steps we will cover include elevating privileges, creating a port forward pivot, and generating a C# payload. This hands-on walkthrough will enhance your understanding of how to effectively use Empire for post-exploitation activities.

## Elevating Privileges
For our Port Forward Pivot to work succesffully, we will need to elevate our agent first. For this part, we will use a simple UAC bypass to achieve this.

1. Return to our agent from Exercise 2 and 3 by selecting it in the Agents tab.

2. Type in `powershell_privesc_bypassuac_fodhelper` or simply `bypassuac` and select the fodhelper module.

<p align="center">
  <img width="461" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/366c8b79-f83f-42f8-8765-d0499604abae">
</p>

3. Once the module is selected you will see the following options available.

<p align="center">
  <img width="458" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/c3742adf-d42b-4cb6-8212-641a97fdb265">
</p>

4. Select the `http` listener for the required option and leave the remaining optional options as the defaults.

<p align="center">
  <img width="293" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/7643021e-df00-4308-8d68-fb8149c7709b">
</p>

5. Once complete, click `Submit` at the bottom of the module page.

6. If successful, you will see a notification on the bottom left of the screen that a new agent checked in.

<p align="center">
  <img src="https://github.com/BC-SECURITY/Empire/assets/20302208/2801693c-af72-4b24-b583-f7a8ff24fe49">
</p>

7. Take note of the agent's name as we will need it for the next section.

## Create a Port Forward Pivot
In this section, we will guide you through the process of establishing a network pivot using an Empire listener. This step will allow us to redirect network traffic from one agent to another, effectively extending our reach into the target network.

1. Return to the Listeners tab in Starkiller.

<p align="center">
  <img src="https://github.com/BC-SECURITY/Empire/assets/20302208/002e67ad-8d61-4d48-b6e5-944ac60d8d2b">
</p>

2. Next, select `Create` from the top right corner.

<p align="center">
  <img src="https://github.com/BC-SECURITY/Empire/assets/20302208/c2fb205c-0fea-491d-bf14-0818a0267c37">
</p>

3. You will be presented with a dropdown menu with the listener options. Type in `port_forward_pivot` or simply `pivot`.

<p align="center">
  <img width="472" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/d07fa482-c390-4f45-b60d-b3f1d5af151f">
</p>

4. Clicking into the Port Forward Pivot will give you the available options that can be updated.

<p align="center">
  <img width="472" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/eb20a084-ec6b-4eb3-af06-06306f22cdea">
</p>

5. The only option that will need to be set for the pivot to work successfully is the Agent that we want to deploy the pivot on. We will use the agent name from the previous section as our Agent. Be sure you are selecting the Elevated Agent as a standard Agent will not work.

<p align="center">
  <img width="353" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/af218300-03a7-4989-823a-c170ffba1ad8">
</p>

6. With the Agent option set, you can now hit `Submit` on the top right corner.

<p align="center">
  <img src="https://github.com/BC-SECURITY/Empire/assets/20302208/5bd90aaf-9f32-4ef4-9dcf-b88f64c901cd">
</p>

7. If there were no issues, you will see a notification on the bottom left of the screen that says `Listener created`.

<p align="center">
  <img width="416" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/b70e1435-65cf-427b-8490-01d70d8ac884">
</p>

## Creating a C# Payload
Now we will cover the process of generating and compiling a C# stager. Empire uses a modified version of the Roslyn compiler from Covenant and has integrated into the project. This tool allows us to transform our C# code into an executable file, specifically designed to invoke PowerShell. The ensuing steps will walk you through the process of specifying the necessary parameters, creating your payload, and ultimately deploying it.

1. Now that the listner is crated, we will navigate back to the Stagers tab.

<p align="center">
  <img src="https://github.com/BC-SECURITY/Empire/assets/20302208/ba9ce4c7-afd0-4d3f-956e-d6e9309f7cad">
</p>


2. Next, select `Create` on the top right of the screen. Then type in `windows_csharp_exe` or simply `exe`.

<p align="center">
  <img width="458" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/be03e24a-c814-41b6-98f6-cb845e258052">
</p>

3. You will see the following options for the C# stager.

<p align="center">
  <img width="467" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/5001c5bb-0723-4664-bb8d-f2b579581aa8">
</p>

4. For this stager, there will be 2 different options that we will be setting. First select the Listener as `port_forward_pivot`. 

<p align="center">
  <img width="235" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/8b68a94b-5116-446c-bbbc-60970cc42669">
</p>

5. Second, select the language as `PowerShell`.

<p align="center">
  <img width="227" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/c69b4d3e-2c5a-4f5b-9b67-d75b7aa40154">
</p>

6. Once those options are set, select `Submit` on the top right of the screen.

<p align="center">
  <img src="https://github.com/BC-SECURITY/Empire/assets/20302208/cac8f14e-7269-458b-ab5f-be3604c73849">
</
