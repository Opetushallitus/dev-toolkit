# Common tools/softwares - terminal

For this project, we strive to use same/similar tools/softwares for each developer's terminal to facilitate smooth and ergonomic shared developer practices. **We do not want to force anyone to use these softwares!** However, **it is highly recommend** to install and use these softwares. This document is divided into an installation part and a reasoning part. In the former, the installation steps here are divided into three main steps. First, installing WSL2 itself (Windows users only, MacOS users can skip this), then installing the rest of the tools/softwares, and lastly finalizing your terminal environment. In the latter part, the reasoning for the choice of software is explained. For the non-terminal based ones, a similar document is found [here](./common-tools-and-softwares-non-terminal.md).

Below is a list of common terminal-based softwares used in this project:

- Windows Subsystem for Linux (WSL2) (Windows users only)
- Node Version Manager (NVM)
- SDKMAN (managing SDKs for the Java Virtual Machine)
  - Java and Maven will be installed as well in this step to get started

If you have opinions on other softwares that you strongly want to use that conflict with any listed here, you are encouraged to discuss it with your team leader!

## Installation

### Step 1: WSL2 (Windows users only)

Before installing any other tools/softwares in this document, begin by installing WSL2. To install WSL2, go to [this page](https://learn.microsoft.com/en-us/windows/wsl/install) and follow the instructions. We recommend installing the default Ubuntu distribution.

As for the terminal, we recommend to use the [Windows Terminal](https://learn.microsoft.com/en-us/windows/terminal/install) application.

### Step 2: Installing the rest of the tools/softwares

#### Node Version Manager (NVM)

To install NVM, open up a terminal and run the following command: `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash`. You can install the latest Node and npm versions by running the command `nvm install node`.

#### SDKMAN

To install SDKMAN, open up a terminal and run the following command: `curl -s "https://get.sdkman.io" | bash`. To get started, you can install the Amazon Corretto JDK v21.0.12 and Maven v3.9.10 by running the commands below. When asked to set them as your default, answer yes.

Amazon Corretto JDK: `sdk install java 21.0.12-amzn`.

Maven `sdk install maven 3.9.10`.

### Step 3: Finalizing your terminal environment

#### GitHub Personal Access Token (PAT) (classic)

Firstly, you need to have a GitHub account that you'll use in this project (you most likely already have one). In this project, we utilize [GitHub Package](https://docs.github.com/en/packages/learn-github-packages/introduction-to-github-packages) to host some of our dependency packages. For the dependency managers to access the registry (npm, Maven etc), you need to add a PAT to their settings.

To create your PAT, follow the instructions on [this page](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic). For the scope, select `read:packages`. **COPY THE TOKEN AFTER IT IS DISPLAYED TO YOU!** You will need it for the next steps.

#### `.bashrc`

First, copy the contents of the `.bashrc`-file found in the `configs`-directory in this repository. Then, in your home directory, open up your `.bashrc` file with your preferred text editor (e.g. `nano ~/.bashrc`). Paste the content you copied earlier to the bottom of the opened file.

For the `GITHUB_TOKEN`-field, paste the GitHub PAT you created earlier within the ""-characters.

For the `BROWSER`-field (Mac users can delete/ignore this as its WSL specific), you need to add a path to your preferred browser that is on the host machine (Windows side). This is done so that the `open` command can work in WSL. Do the following:

1. Find the Windows path to your preferred browser. Usually, they are in your `C:\Program Files\`-directory. E.g., Chrome is at the path `C:\Program Files\Google\Chrome\Application\chrome.exe`
2. In your home directory, create a symbolic link to the Windows path by running the command `ln -s <path>`. E.g., with Chrome it is `ln -s /mnt/c/Program\ Files/Google/Chrome/Application/chrome.exe`. NOTE! Spaces are escape with a `\` character
3. Open up your `.bashrc`-file again, and replace the text inside the ""-characters with `$HOME/<browser>.exe`. E.g., with Chrome it is `$HOME/chrome.exe`

#### Maven settings

First, copy the contents of the `maven-settings.xml`-file found in the `configs`-directory in this repository. Then, assuming you have installed Maven as in the previous steps, open up the file located in `~/.m2/settings.xml` with your preferred editor. If the file doesn't exist, create it. Paste the content you copied earlier. Add your GitHub username and your PAT to the correct fields.

#### Npm settings

First, copy the contents of the `.npmrc`-file found in the `configs`-directory in this repository. Then, open up the file located in `~/.npmrc` with your preferred editor. If the file doesn't exist, create it. Paste the content you copied earlier. Add your PAT to the correct field.

## Reasoning

### WSL2 (Windows users only)

If you are using a Windows machine, **it is highly recommended to use [WSL2](https://learn.microsoft.com/en-us/windows/wsl/about).** WSL2 allows you to run a Linux environment on your Windows machine without the need for a separate virtual machine or dual booting. The reasoning for why we **strongly recommend using WSL2** are the following:

- Linux is Unix-based, while Windows is not. Every script that has been written throughout the many years at OPH have been written in Bash, which is supported by Unix-based systems. **Scripts written in Bash cannot be run directly on Windows systems**, hence it would require us to rewrite them all to support e.g. Powershell.
- Other developers in this project use MacOS, which is also Unix-based. If the Windows users use WSL2, interoperability between Windows and MacOS developers is significantly better.
- Getting comfortable and efficient with using Unix-based systems is an important skill for a developer, as the vast majority of servers run on Linux. All of the servers in this project are run using Linux.

### Node Version Manager (NVM)

The reasoning for using NVM is:

- Well supported and used Node version manager
- Several services use different Node versions
- NVM is already used in many services

### SDKMAN

The reasoning for using SDKMAN is:

- Having one way to manage the different SDK versions allows for automatic scripting for running services locally. For example, instead of trying to determine all the possible ways to manage different Java versions - such as using _update-java-alternatives_, _update-alternatives_, or _galternatives_ - we choose one way and use that. It makes maintainability much better
- This has already been done in _Yleiskäyttöiset palvelut (YK)_. All the different services uses SDKMAN to select the correct Java version locally (at least for WSL2 users). An example can be found [here](https://github.com/Opetushallitus/organisaatio/blob/master/scripts/lib/common-functions.sh#L120-L165).
