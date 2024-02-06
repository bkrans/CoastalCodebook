# Installation

For the tuturial sessions we will use an interactive computing environment, that is built
on the [Jupyter]() ecosystem and mostly rely on software that is supported by numfocus. We will communicate the tutorial content
using `git` version control and provide instructions on how to do so using the GitHub client. In the subsections
that follow we talk you through the three configurations steps.

### 1. Git

If you are not familiar with using Git, please have a look this short but excellent
[introduction](https://earth-env-data-science.github.io/lectures/environment/intro_to_git.html)
first.

1. Please refer to the [GitHub Client documentation](https://desktop.github.com/) to
   install the GitHub client, or see [these
   instructions](https://github.com/git-guides/install-git) to install git using the
   command line.
2. Clone this repository to your local
   computer using either of the following options.

   1. **GitHub client**: Browse to the
   [webpage](https://github.com/FlorisCalkoen/CoastalCodebook), click on the green "Code"
   button and select "Open with GitHub Desktop"; or simply paste the URL into the GitHub
   client "clone repository" menu.

   2. **Bash shell**: If you have a bash terminal available, assuming that git [is
     configured](https://docs.github.com/en/get-started/getting-started-with-git), you
   can simply run: ` git clone https://github.com/FlorisCalkoen/CoastalCodebook.git`.

3. GitHub client does not install the underlying git software on your machine. Follow [these
   instructions](https://learn.microsoft.com/en-us/devops/develop/git/install-and-set-up-git)
   to install git on your machine.


By these steps, the files that are hosted at GitHub are "pulled" to your machine. You can
check that by opening a file explorer and going to the path where you cloned the
directory. The files that you find there should reflect what's on the GitHub page.
But we can't we do anything with the files yet, as we don't have the software that can
understand the code, so we will continue with installing a package manager.

### 2. Mamba package manager

If you're not familiar with managing Python environments, please have a look at this
[introduction](https://earth-env-data-science.github.io/lectures/environment/python_environments.html?highlight=conda)
first. The bottom line is that it is good practice to manage your software environments
to avoid dependency conflicts. For the tutorial notebooks,  we recommend to use the
lightweight package manager `mambaforge`. The instructions to install this package
manager can be found in [their
documentation](https://mamba.readthedocs.io/en/latest/installation.html), in which they
refer to the [Conda Forge GitHub](https://github.com/conda-forge/miniforge#mambaforge)
page to download the software.

#### Windows

1. Download the mambaforge executable file for Windows from [Miniforge GitHub
page](https://github.com/conda-forge/miniforge#mambaforge). On that page there are also
binaries for Mac and Linux; and for `conda` package managers, so make sure you download
the `mambaforge` executable file for Windows. Install the executable by clicking on it;
you can stay with the default settings by just clicking next through the installation
client.
2. Now that mambaforge is installed, you can open a `Miniforge Prompt`. You can open this
   shell by opening the start window and search for "Miniforge".

**Known issues**: Some users have their firewalls configured in such way that the
mambaforge installation is blocked. If you have trouble installing mambaforge, please make
sure to temporarily disable your firewall.

#### Unix like - Mac and Linux
1. We recommend to install Mambaforge on Linux and Mac using a terminal. On Mac, you can
   open a terminal by searching for "terminal" or "iterm". On Linux the hotkey to open a
   terminal is "cntrl + shift + t". The commands to
   install the package manager are copied from their documentation and can be run by
   copying the commands below over to your terminal and pressing enter:
   ```bash
   curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Mambaforge-$(uname)-$(uname -m).sh"
   bash Mambaforge-$(uname)-$(uname -m).sh

   ```
2. Accept the user agreements, and allow the installation script to edit your profile
   file. The profile file (`~/.bashrc` on Linux or possibly `~/.zshrc` on Mac) is the
   first script which is being executed when you open a new terminal. The installation
   script will add a few lines to that file to make the `mamba` command available every
   time open a new terminal.
3. Close the terminal.

### 3. Software environments
To run the tutorial notebooks we need several packages. To avoid dependency conflicts it
is good practice to seperate your environments; that was the reason for installing a
package manager. Now that we have our package manager we will create the software
environments. We will create one environment that runs the JupyterLab IDE, including
several extensions; and another one that contains the packages that we need for the
tutorials.

1. Now that mambaforge is available on your machine, open a terminal. On Windows you
   should open the Miniforge prompt, which you can find by searching for it in the Start
   window. On Mac you can open a terminal by searching for "terminal" or "iterm". For
   Linux it's "cntrl + shift + t".
2. You can check if mamba was installed by running the following command in the terminal:
   ```bash
   mamba --version

   ```
   It should output something like:

   ```console
   ~ (base) mamba --version
   mamba 1.1.0
   conda 22.9.0
   ```

3. Now that mambaforge is installed, navigate in the terminal to the directory
   where you cloned the GitHub CoastalCodeBook repository. You can navigate the terminal
   using `cd`, which stands for "change directory".
   - **Windows**: if you are on Windows and you installed the GitHub client using their default settings you can
   simply run `cd %userprofile%\Documents\GitHub\CoastalCodeBook`.
   - **Linux/Mac**: change to the directory where you cloned the GitHub repository. This
     will be something like `cd ~/path/to/github/repository`.
4. The CoastalCodeBook root directory contains an [environment.yml](environment.yml) file that describes the software
   dependencies. This environment contains several packages and extension to build an
   interactive Jupyter lab environment that you can use to run the tutorial notebooks.

   You can create the software environment using this command:

   ```bash
   mamba env create -f environment.yml
   ```