# Agent Chaining


## Elevating Privileges
For our Port Forward Pivot to work succesffully, we will need to elevate our agent first. For this part, we will use a simple UAC bypass to achieve this.

1. Return to our agent from Exercise 2 and 3 by selecting it in the Agents tab.

2. Type in `powershell_privesc_bypassuac_fodhelper` or simply `bypassuac` and select the fodhelper module.

<img width="461" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/366c8b79-f83f-42f8-8765-d0499604abae">

3. Once the module is selected you will see the following options available.

<img width="458" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/c3742adf-d42b-4cb6-8212-641a97fdb265">

4. Select the `http` listener for the required option and leave the remaining optional options as the defaults.

<img width="293" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/7643021e-df00-4308-8d68-fb8149c7709b">

5. Once complete, click `Submit` at the bottom of the module page.

6. If successful, you will see a notification on the bottom left of the screen that a new agent checked in.

![image](https://github.com/BC-SECURITY/Empire/assets/20302208/2801693c-af72-4b24-b583-f7a8ff24fe49)

7. Take note of the agent's name as we will need it for the next section.

## Create a Port Forward Pivot

1. Return to the Listeners tab in Starkiller.

![image](https://github.com/BC-SECURITY/Empire/assets/20302208/002e67ad-8d61-4d48-b6e5-944ac60d8d2b)

2. Next, select `Create` from the top right corner.

![image](https://github.com/BC-SECURITY/Empire/assets/20302208/c2fb205c-0fea-491d-bf14-0818a0267c37)

3. You will be presented with a dropdown menu with the listener options. Type in `port_forward_pivot` or simply `pivot`.

<img width="472" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/d07fa482-c390-4f45-b60d-b3f1d5af151f">

4. Clicking into the Port Forward Pivot will give you the available options that can be updated.

<img width="472" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/eb20a084-ec6b-4eb3-af06-06306f22cdea">

5. The only option that will need to be set for the pivot to work successfully is the Agent that we want to deploy the pivot on. We will use the agent name from the previous section as our Agent. Be sure you are selecting the Elevated Agent as a standard Agent will not work.

<img width="353" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/af218300-03a7-4989-823a-c170ffba1ad8">

6. With the Agent option set, you can now hit `Submit` on the top right corner.

![image](https://github.com/BC-SECURITY/Empire/assets/20302208/5bd90aaf-9f32-4ef4-9dcf-b88f64c901cd)

7. If there were no issues, you will see a notification on the bottom left of the screen that says `Listener created`.

<img width="416" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/b70e1435-65cf-427b-8490-01d70d8ac884">

## Creating a C# Payload
1. Now that the listner is crated, we will navigate back to the Stagers tab.

![image](https://github.com/BC-SECURITY/Empire/assets/20302208/ba9ce4c7-afd0-4d3f-956e-d6e9309f7cad)


2. Next, select `Create` on the top right of the screen. Then type in `windows_csharp_exe` or simply `exe`.

<img width="458" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/be03e24a-c814-41b6-98f6-cb845e258052">

3. You will see the following options for the C# stager.

<img width="467" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/5001c5bb-0723-4664-bb8d-f2b579581aa8">

4. For this stager, there will be 2 different options that we will be setting. First select the Listener as `port_forward_pivot`. 

<img width="235" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/8b68a94b-5116-446c-bbbc-60970cc42669">

5. Second, select the language as `PowerShell`.

<img width="227" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/c69b4d3e-2c5a-4f5b-9b67-d75b7aa40154">

6. Once those options are set, select `Submit` on the top right of the screen.

![image](https://github.com/BC-SECURITY/Empire/assets/20302208/cac8f14e-7269-458b-ab5f-be3604c73849)

7. If the stager was successfully generated, you will be given the option to download it at the top of the screen.

![image](https://github.com/BC-SECURITY/Empire/assets/20302208/8f26a3e1-762c-46d5-95ab-5acf2830ffb3)

8. Once you have downloaded the payload, we will navigate to the website `http://10.10.0.194/upload` in our browser.

<img width="421" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/c8936f6c-b76f-480d-b598-d4c4c7bb06dc">

9. On this page, you will be given the option to upload a file for "review". CLick on the Browse Button on the page.

![image](https://github.com/BC-SECURITY/Empire/assets/20302208/51bf9978-be49-479f-8094-fa450b5f4fa0)

10. Browse to the `Downloads` directory and select `Sharpire.exe`.

<img width="404" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/6e1042eb-ea56-4731-b225-f9a38ed23e74">

11. Finally, click `Upload` to upload the file to the Web Server.

![image](https://github.com/BC-SECURITY/Empire/assets/20302208/3d57915b-dab3-43a1-95bf-d6bb9bcf81e3)

12. If you are successful, you will receive a new Agent with the following information.

![image](https://github.com/BC-SECURITY/Empire/assets/20302208/d756b5c0-4006-4952-a0d1-296a8da3319d)

13. You can also view the agents using the Graph View in Starkiller to see which agents are chained together by clicking `Graph` at the top of the Agents tab.

![image](https://github.com/BC-SECURITY/Empire/assets/20302208/cc49225e-0f8d-49a5-8a99-264851f1462b)

14. Once selected, you will see a graphical representation of the Agents.

<img width="373" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/31dcc9f3-4a69-43d6-8a5c-abc733d28e6b">