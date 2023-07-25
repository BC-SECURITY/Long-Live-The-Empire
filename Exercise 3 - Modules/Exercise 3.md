# Exercise 3: Module Execution
For this exercise, we will use the Kali box and Workstation 1.

we delve into the practical aspects of module execution. We'll start by operating an interactive shell, proceeding to list and inject processes, then moving on to executing Binary Object Files (BOF). Finally, we'll explore privilege escalation through a common User Account Control (UAC) bypass technique.

## Interact with Agent
On the Agents tab of Starkiller, click on the name of the agent to interact with it.

![image](https://github.com/BC-SECURITY/Empire/assets/20302208/d27644f3-1ce4-4533-bf33-99bbddc4e84c)

Once you have clicked on the agent, you will be given numerous options for interaction.

<img width="781" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/5cd9d2b7-08c7-4887-b786-8a3202483ea7">

## Interactive Shell
1. Enter the interactive shell by clicking the arrow on the top right corner.

    ![image](https://github.com/BC-SECURITY/Empire/assets/20302208/f7b0e22a-6e09-4b2f-9557-fd7c86914382)

2. Once you click the arrow, you will be presented with a shell-like interface. 
    <img width="790" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/85923a63-7767-4687-abc6-427f698a3e26">

3. Type `whoami` and see the following result.

    <img width="155" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/d8dd0187-dab3-4484-9f29-a8ddeb26c87a">

4. Now enter, `cd ..` which will change your current working directory. However, When entering a command, keep in mind there may be a delay due to the beacon interval that is set.

    <img width="157" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/3c75569c-55a2-4577-8976-f05c445d8b17">

## List Processes and Injection
1. At the top of the agent interaction page, there is a tab named Processes.

    ![image](https://github.com/BC-SECURITY/Empire/assets/20302208/da2e4d0e-3673-4cc2-93b6-8f1132571ec2)

2. Open Notepad on Workstation 1

3. The process list is shared across all agents that are on the same workstation. So, pressing the refresh button will refresh the process list for all agents sharing the same machine.

    ![image](https://github.com/BC-SECURITY/Empire/assets/20302208/09ef5658-846c-49f8-a35f-31f057145209)

4. Find Notepad on the workstation by typing `notepad` into the search bar.

    <img width="558" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/b5347c30-0ba6-4256-9b1d-91960ae6c1ca">

5. Now click on the arrow on the right side of the process and select the `powershell_management_psinject`. This will allow us to inject directly into this process without having to navigate back to the main execution page of the agent.

    ![image](https://github.com/BC-SECURITY/Empire/assets/20302208/ff22fa1d-52cd-40ef-9ddf-a56338d08a5b)

6. Once Psinject is selected, you will have the option to make changes to the module before executing. We will not need to make any changes in this case and can scroll to the bottom and click `submit`.

    <img width="211" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/80e73ff7-7917-42ca-9bf8-524229e62c08">

## BOF Execute
This script will load the BOF file (aka COFF file) into memory, map all sections, perform relocation, serialize beacon parameters, and jump into the entry point selected by the user. Empire uses [RunOF](https://github.com/nettitude/RunOF) for executing BOFs and compiles the executable at runtime.

1. Navigate back to the main interaction page of the agent by selecting the `Interact` tab.

    ![image](https://github.com/BC-SECURITY/Empire/assets/20302208/5a3c8d64-c380-4c98-a679-d62df82de251)

2. Click on the `Execute Module` module window and type `csharp_inject_bof_inject_bof` or simply `bof`.

    <img width="529" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/810947b0-9add-4af2-a387-de1bc9ad7dce">

3. Enter the module and you will see the following options.

    <img width="484" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/75433632-8c10-46bb-94c9-47c0fc43f0ab">

4. The only option that will need to be updated for this example is that we need to provide a BOF file for the module to execute. 

5. Click on the upload arrow next to `File`.

    ![image](https://github.com/BC-SECURITY/Empire/assets/20302208/7176b12a-18ca-4906-80fd-06b075a5bbe9)

6. Then click the paperclip.

    ![image](https://github.com/BC-SECURITY/Empire/assets/20302208/c88e94e7-01fb-497c-9521-ad9f871095f3)

7. A popup window will open and you will need to navigate to `Downloads`, select the file `whoamix64.o`, and click `Open`.

    <img width="420" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/944876f1-682b-4f12-801a-3d1fc53fa9e6">

8. Starkiller will give you the option to make changes to the file. However, we are going to leave the defaults and click `Upload`.

    <img width="409" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/b3b6cd68-28c7-4c5d-a441-495230514cc2">

9. The module will now show our BOF as the file that is ready to execute.

    ![image](https://github.com/BC-SECURITY/Empire/assets/20302208/0da55a81-33b1-4f31-bb0d-c5182733e217)

10. Click `Submit` at the bottom of the module.

11. Next, click the `Tasks` tab at the top of the Agent.

    ![image](https://github.com/BC-SECURITY/Empire/assets/20302208/395f80c4-489c-443f-8a7b-6e6678403069)

12. You will be given a list of tasks that have been executed on our agent thus far.

    <img width="670" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/8fdd4fba-df5b-4e24-8e3a-8f8c57e6ac65">

13. Click on the most recent task and view the output from the BOF execution.

    ![image](https://github.com/BC-SECURITY/Empire/assets/20302208/1bc98184-1357-4d11-8179-1790d2c69c46)

14. You can also select other actions by clicking the three dots to the right of a task, where you can download the code that was executed on the agent and the output.

    <img width="520" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/a15d612c-c678-4d36-8632-3b1c4325f0eb">
