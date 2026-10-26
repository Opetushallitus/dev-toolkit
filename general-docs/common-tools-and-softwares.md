# Common tools/softwares

For this project, we strive to use same/similar tools/softwares for each developer to facilitate smooth and ergonomic shared developer practices. Below is a list of common softwares used in this project

- Windows Subsystem for Linux (WSL2) (Windows users only)
- OpenAI ChatGPT and Codex (AI tools)
- Rancher Desktop (GUI for Docker) or Docker Engine in WSL2

**We do not want to force anyone to use these softwares!** However, **it is highly recommend** to install and use these softwares if they fulfill a need of yours. Installation steps and the reasoning for the choice of software in their respective use case is explained under the subheading for each software separately.

If you have opinions on other softwares that you strongly want to use that conflict with any listed here, you are encouraged to discuss it with your team leader!

## Windows Subsystem for Linux (WSL2) (Windows users only)

If you are using a Windows machine, **it is highly recommended to use [WSL2](https://learn.microsoft.com/en-us/windows/wsl/about).** WSL2 allows you to run a Linux environment on your Windows machine without the need for a separate virtual machine or dual booting.

### Reasoning

The reasoning for why we strongly recommend using WSL2 are the following:

- Linux is Unix-based, while Windows is not. Every script that has been written throughout the many years at OPH have been written in Bash, which is supported by Unix-based systems. **Scripts written in Bash cannot be run directly on Windows systems**, hence it would require us to rewrite them all to support e.g. Powershell.
- Other developers in this project use MacOS, which is also Unix-based. If the Windows users use WSL2, interoperability between Windows and MacOS developers is significantly better.
- Getting comfortable and efficient with using Unix-based systems is an important skill for a developer, as the vast majority of servers run on Linux. All of the servers in this project are run using Linux.

### Installation

To install WSL2, go to [this page](https://learn.microsoft.com/en-us/windows/wsl/install) and follow the instructions. We recommend installing the default Ubuntu distribution.

As for the terminal, we recommend to use the [Windows Terminal](https://learn.microsoft.com/en-us/windows/terminal/install) application.

## OpenAI ChatGPT and Codex

For our AI tools, we utilize the services provided by OpenAI, such as ChatGPT and Codex. You most likely have already read our [guide](https://eu.sharepoint.ent.cgi.com/sites/CL16586/Shared%20Documents/CGI%20devloper%20guides) on how to apply for these two softwares. If not, go to that page and do so. For brevity's sake, the reasoning and installation guide will be omitted from here.

## Rancher Desktop or Docker Engine in WSL2

In this project, we utilize containerization with Docker. Docker does not come packaged by default with WSL2. To use Docker in WSL2, there are two options: installing [Rancher Desktop](https://rancherdesktop.io/) if you want to use a GUI when working with containers, or installing the Docker Engine directly into WSL2 if you primarily interact with Docker using the CLI. **Choose one of the two methods**, as if you do both, unexpected behaviors can occur.

### Reasoning

The reasoning for using Docker in either way are the following:

- For GUI usage: Rancher Desktop is a free and open-source alternative to Docker Desktop. Additionally, Docker Desktop requires a license to use.
- For CLI usage: The only supported way to only use the CLI with Docker is through installing the Docker Engine directly into WSL2

### Installation

#### Rancher Desktop

Go to [this page](https://rancherdesktop.io/) and select the Windows installer. Once that is done, run the installer and follow the instructions. When the installation wizard asks you which container engine to use, select _moby_.

Once you are done, open up Rancher Desktop, and click _Preferences_ > _WSL_ > make sure the WSL2 distribution you installed is selected. An image below shows an example of how it looks like:

![rancher-wsl-enable](./images/rancher-wsl-enable.png)

To verify that it is working, open up a WSL2 terminal instance and run the command `docker --help`. If it succeeds, you are done.

#### Docker Engine

To install Docker Engine in WSL2 with Ubuntu, go to [this page](https://docs.docker.com/engine/install/ubuntu/). For the installation method, **go with the [Install using the apt repository](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository) method!** After you've verified that you have successfully installed and started Docker Engine, go to the [Linux Postinstall step](https://docs.docker.com/engine/install/linux-postinstall). You only need to complete the _Add your user to the docker group_ step.
