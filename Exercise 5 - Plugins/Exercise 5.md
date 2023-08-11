# Exercise 5: Plugins

To learn more about plugins, see the [Empire Wiki](https://bc-security.gitbook.io/empire-wiki/plugins/plugin-development).

## Clone the plugin
For this exercise we are going to use the [https://github.com/BC-SECURITY/AutoRun-Plugin](AutoRun-Plugin).

```bash
cd empire/server/plugins
git clone git@github.com:BC-SECURITY/AutoRun-Plugin.git
```

## Restart the server
Use Ctrl+C to stop the server and then run `./ps-empire server` again.

## Check the plugin in Starkiller
Navigate to the [Starkiller plugins page](http://localhost:5173/#/plugins).

Click on the `AutoRun-Plugin` plugin.

We aren't going to change anything, but note that the `Shell Command` field is set to `ps`.

## Launch a new agent
Follow the steps from [Exercise 2](../Exercise%202%20-%20Deployment%20Basics/Exercise%202.md)'s `Deploy the Agent` section to launch a new agent.

## Check the agent's tasks
Note that the agent automatically executed a `ps` command.