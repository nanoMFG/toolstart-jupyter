# toolstart-jupyter
Template repository for a nanoHUB tool that uses a Jupyter notebook frontend.

## Getting Started
The following procedure describes how to get a basic jupyter notebook "tool" up and running on [nanoHUB](https://nanohub.org). 
It is assumed you are a registered user and developer on nanoHUB and intend to install and publish your notebook content there.
Refer to the *whypublish* links below for details on why and how to publish content on nanoHUB.  

1. Create a new GitHub repository and select `toolsart-jupyter` as a template.  
See: [Creating a Repository From a Template](https://docs.github.com/en/free-pro-team@latest/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template)
2. Create a new tool page on nanoHUB using the [nanoHUB tool creation form](https://nanohub.org/tools/create)  
  - Set the Repository Host Option to "Host GIT repository on GitHUB"
  - Set the Repository Url to your GitHub repo:  
    Public URL: `https://github.com/yourgithubrepo`  
    Private URL: `ssh://github.com/yourgithubrepo`
3. Edit the `/middleware/invoke` file as follows:  
- Determine whether the tool will run as an ordinary notebook or in *app mode*, adjust the `start_jupyter` option as needed.  See **App Mode vs Sequential Notebook** below for more details.  
- Edit the `-T @tool mytool.ipynb` part to match the actual name of your notebook.
- Edit the `-t mytool \` part to match the "short name" of the tool as created on nanohub via the [nanoHUB tool creation form](https://nanohub.org/tools/create).

## App Mode vs Sequential Notebook
Notebooks that are published with the `-A` option to the `start_jupyter` command or will launch in in *app mode* which will cause them to execute in their entirety when launched.  This is primarily intended for tools that deploy an [ipywidjets](https://ipywidgets.readthedocs.io/en/latest)/event-based user interface.

Notebooks published without the `-A` option to the `start_jupyter` command will deploy ad standard hosted jupyter notebooks that can be executed and edited by the user.

## References
https://jupyter.org/  
https://nanohub.org  
https://nanohub.org/whypublish  
https://nanohub.org/whypublish/whypublishhowtostart  
https://nanohub.org/whypublish/whypublishdeployjupyter  
https://ipywidgets.readthedocs.io/en/latest  
https://github.com/hubzero/hublib

### start_jupyter options
```
 $ start_jupyter --help
usage: usage: start_jupyter [-h] [-t] [-c] [-d] [-A] [-T dir] [name]

Start a Jupyter notebook-based tool

positional arguments:
  name        Name of notebook to run.  The terminal and
              dashboard (tree view of files) will de disabled.

              If no name is given, a notebook server will
              be started in the current directory.  Terminal
              and dashboard will be enabled.

optional arguments:
  -h, --help  show this help message and exit.
  -d          Show debug (verbose) output.
  -t          Run as a Tool with no notebook controls.
  -c          Copy instead of link notebook files.
  -A          Run in AppMode.
  -T dir      Search for notebook starting in dir.
  ```
  ### invoke_app options*
```
-A tool arguments
 -c execute command in background
 -C command to execute for starting the tool
 -e environment variable (${VERSION} substituted with $TOOL_VERSION)
 -f No FULLSCREEN
 -p add to path          (${VERSION} substituted with $TOOL_VERSION)
 -r rappture version
 -t tool name
 -T tool root directory
 -u use envionment packages
 -v visualization server version
 -w specify alternate window manager
 ```
*source: [https://help.hubzero.org/documentation/22/tooldevs/invoke](https://help.hubzero.org/documentation/22/tooldevs/invoke)
