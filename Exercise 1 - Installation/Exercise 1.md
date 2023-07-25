# Exercise 1: Empire Installation and Startup
The Empire Server is pre-installed on the Kali Linux machine in the lab. However, the installation instructions are found on the [Empire Wiki](https://bc-security.gitbook.io/empire-wiki/quickstart/installation).
The Kali machine is located at `10.10.2.70`

# Empire Installation
We recommend using the GitHub installation on Kali LInux for running Empire. Below are the instruction for pulling and installing from [GitHub](https://github.com/BC-SECURITY/Empire).
```bash
git clone --recursive https://github.com/BC-SECURITY/Empire.git
cd Empire
./setup/checkout-latest-tag.sh
sudo ./setup/install.sh -y
```

If Empire successfully installs, you will see a message similar to the one below.

<img width="315" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/2faad832-29a8-4e4e-9044-3d992e440fdf">

# Starting Empire
Empire comes pre-built with a server and client. The server manages all aspects of Empire, while the client is a command line tool for connecting to Empire. The client is considered the old method for using Empire and Starkiller is the recommend and preferred method of using Empire.

## Help Menu
```
./ps-empire --help                                                   
usage: empire.py [-h] {server,client,sync-starkiller} ...

positional arguments:
  {server,client,sync-starkiller}
    server              Launch Empire Server
    client              Launch Empire CLI
    sync-starkiller     Sync Starkiller submodule with the config

options:
  -h, --help            show this help message and exit
```
## Start Server
The teamserver is the essential part for Empire and can be started by running the script `./ps-empire server`. If the serve has started up successfully you will see various messages mentioning the loading of templates, listeners, bypasses, malleable profiles, modules, and plugins. Then finally you will see a notification that Starkiller and Uvicorn are running.

<img width="445" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/e061b0a3-4667-4ef8-8c9b-f19b9bf337a7">

**Note:** You may see other messages as the server starts up for the first time. Don't worry as they are the server setting up the Roslyn compiler and Starkiller.

### Help Menu
```
./ps-empire server --help
usage: empire.py server [-h] [-l {DEBUG,INFO,WARNING,ERROR,CRITICAL}] [-d]
                        [--reset] [-v] [--config CONFIG] [--secure-api]
                        [--restip RESTIP] [--restport RESTPORT]

options:
  -h, --help            show this help message and exit

General Options:
  -l {DEBUG,INFO,WARNING,ERROR,CRITICAL}, --log-level {DEBUG,INFO,WARNING,ERROR,CRITICAL}
                        Set the logging level
  -d, --debug           Set the logging level to DEBUG
  --reset               Resets Empire's database and deletes any app data
                        accumulated over previous runs.
  -v, --version         Display current Empire version.
  --config CONFIG       Specify a config.yaml different from the
                        config.yaml in the empire/server directory.
  --secure-api          Use https for the API. Uses .key and .pem file from
                        empire/server/data.Note that Starkiller will not
                        work with self-signed certs due to browsers
                        blocking the requests.

RESTful API Options:
  --restip RESTIP       IP to bind the Empire RESTful API on. Defaults to
                        0.0.0.0
  --restport RESTPORT   Port to run the Empire RESTful API on. Defaults to
                        1337
```

## Start Client
As mentioned earlier, the client is the old method of connecting to Empire and can be launched using `./ps-empire client`.

### Help Menu
```
./ps-empire client --help
usage: empire.py client [-h] [-l {DEBUG,INFO,WARNING,ERROR,CRITICAL}]
                        [-r RESOURCE] [--config CONFIG] [--reset]

options:
  -h, --help            show this help message and exit
  -l {DEBUG,INFO,WARNING,ERROR,CRITICAL}, --log-level {DEBUG,INFO,WARNING,ERROR,CRITICAL}
                        Set the logging level
  -r RESOURCE, --resource RESOURCE
                        Run the Empire commands in the specified resource
                        file after startup.
  --config CONFIG       Specify a config.yaml different from the
                        config.yaml in the empire/client directory.
  --reset               Resets Empire's client to defaults and deletes any
                        app data accumulated over previous runs.
```

## Open Starkiller
A separate application is no longer required for running Starkiller since Empire now hosts service. It is simple to connect to locally or remotely.

1. Open a web browser and navigate to `http://localhost:1337/index.html`. You may connect using the listed address on the server, however, non-local connections may have some functionality disabbled.

    <img width="322" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/5a939a2e-764b-4c1f-a718-d29cde00e41d">

2. Type in the following information:
    - Username: `empireadmin`
    - Password: `password123`

    <img width="218" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/d4b2ae66-ddbd-4f02-8c55-59abca9cb01e">

3. If login is successful, you will have access to Starrkiller.

    <img width="842" alt="image" src="https://github.com/BC-SECURITY/Empire/assets/20302208/919e5d49-db36-42b0-9990-7a10bea8262c">


