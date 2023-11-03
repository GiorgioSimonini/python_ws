# python_ws - Python workspace for robotics

<!-- ![intro image](./media/intro_image) -->
`WORKSPACE UNDER DEVELOPMENT!!!`

Docker workspace to use Python on Ubuntu 22.04. It includes a local installation of the Peter Corke [Robotics Toolbox](https://github.com/petercorke/robotics-toolbox-python) and other usefull libraries.

## Table of Contents
1. [Requirements](#Requirements)
1. [Installation](#Installation)
   1. Windows
   1. Linux
1. [Note](#Note)

## Requirements
The virtual environment requires a linux system (or subsystem using [WSL](https://ubuntu.com/wsl) on Windows). It also require:
* [git](https://git-scm.com/)
* [docker](https://www.docker.com/)
* [vscode](https://code.visualstudio.com/) with [devcontainer](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension

## Installation
Clone the repository wherever you want

	git clone --recursive https://github.com/GiorgioSimonini/python_ws.git

open the folder `python_ws` with `vscode` and click on `Rebuild and Reopen in Container` or use `ctrl+shift+P` to do the same.

## Note
Folder src/ into the python_ws folder is ignored on git, use submodules or other repositories to have source control.

### To connect console to a jupiter notebook
To connect to an existing notebook kernel from a console use

	%connect_info

on a code cell and execute
 
 	jupyter console --existing kernel-###.json

on a terminal using the kernel info ```###```

