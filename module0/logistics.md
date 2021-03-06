# Setting up a working environment
In order to work on the assignments and get the most out of the is course you need a good working environment. The basic requirements for that are a computer and internet access (every now and then).

You need to download the course material in form of a `github` repository, and then, to work on the assignments, you need to install the required python packages on your computer. In case installing the required packages is not possible on your computer, or, for some reason, your computer is not able to run simulations you need in the assignments, we provide a backup in form of a `jupyter hub` (see below for more details).

## Cloning this repository
All the course material will live in this repository. Thus, you will need to install `git`, connect it to your `github` account and clone this repository.
In order to do this:

1. [Install `git`](https://git-scm.com/downloads) on your machine.
2. Connect the local `git` application to your github account by [setting your username and email](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration)
3. (Optional): If you are familiar with ssh authentification, or want to learn about it, you can set it following [these instructions](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) (with ssh authentification enabled you don't have to enter your password for every push and pull). But it is fine to just skip this step.
4. Now you can clone the course repository via

    ```
    git clone https://github.com/cne-tum/lsmlsda2020.git
    ```
(or `git clone git@github.com:cne-tum/lsmlsda2020.git` via ssh). This downloads (clones) the repository folder `lsmlsda2020` into the folder you are currently in, probably your `/home` folder.

## Installing required packages
You need [`anaconda` or `miniconda`](https://docs.conda.io/en/latest/miniconda.html#) to set up the programming environment for this course. With `conda` you
can define [environments](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#) with fixed versions of all required python packages so that reproduction and collaboration becomes easier. The `environment.yml` file in this repository contains packages required for this course. You can create a new `conda` environment from this file by navigating to your local copy of this repository and executing
```bash
conda env create -f environment.yml
```
Have a look at the `environment.yml` to see the list of required packages. Once the environment is installed you can activate it via
```bash
conda activate lsmlsda
```
where `lsmlsda` is the name of the environment. Note that the name is set automatically in `environment.yml`.

After activating the `lsmlsda` environment you can start working with the code in this repository and start working on your project.

### Windows user
If you are using windows you have to install two additional packages. After installing and activating the `lsmlsda` environment (above), install the
additional packages via:
```bash
pip install pypiwin32
python -m ipykernel install --user
```
If things do not work or you have any questions, do not hesitate to ask us or or [create an issue](https://github.com/cne-tum/lsmlsda2020_int/issues/new) in repository.

If the installation on your computer can't be fixed in a reasonable amount of time, consider using the `Jupyter Hub`.

In order to run Brian2 simulations, you will need to install C++ Build tools. For that, download Visual Studio here: https://visualstudio.microsoft.com/fr/downloads/, then in VS installer go to "individual components" and select "C++ Build Tools". You will need to have some free space on your disc (~3GB).


## GitHub classroom
We will use GitHub classroom for all assignments. For each module, we will send out a link. By clicking on this link, GitHub will automatically create a repository to which only you and all teaching assistants have access. The last commit in this repository before the deadline will automatically be saved as your submission.


## Jupyter Hub
We set up a [jupyter hub](https://jupyter.org/hub) - a jupyter environment that is running on our servers. In the jupyter hub you have access to powerful CPUs and GPUs so that running the computations needed for your projects in this course
are no problem. Of course, **you must not use the jupyter hub for other projects - resources are limited per user and should be used for this course only**.

The jupyter hub is reachable under [https://bhrigu.cne.ei.tum.de/hub](https://bhrigu.cne.ei.tum.de/hub/login) when you are in the [TUM VPN](https://www.lrz.de/services/netz/mobil/vpn_en/). Once you have logged in via your TUM ID and password you are in the common jupyter notebook environment in which you can create
notebooks, create text files and open a terminal. Upon your first login a Ubuntu user account is created on our server. The terminal lets you access this account via the command line. Using the terminal you can therefore create your desired folder structure, clone and install this repository (`git` and `anaconda` are installed already) etc and start working on your projects. You can find detailed instructions below. Logging into the server and getting set up will also be part of your assigment after the introductory session.

Again, let us know if you have any questions, or [create an issue](https://github.com/cne-tum/lsmlsda2020_int/issues/new).


### Logging in to Jupyter Hub server

  We have set up a jupyterhub compute server on which you can run code, in case you do not have sufficient compute resources of your own.

  Following the steps here, you should be able to log in to the server, and run code in jupyter notebooks or via the terminal.

1. If you don't have a VPN client program for connecting to TUM VPN yet, then download and install the Cisco AnyConnect VPN client from [LRZ](https://www.lrz.de/services/netz/mobil/vpn_en/anyconnect_en/). If the automatic download does not work, you can also manually download the installation files from [here](https://www.lrz.de/services/netz/mobil/vpnclient/)

2. Fire up the VPN-Client and enter your TUM ID and password to connect.

3. Use your favourite browser to navigate to https://bhrigu.cne.ei.tum.de . At the log-in prompt, enter your TUM ID and password again.

4. After login you see the common jupyter notebook environment. In the top right corner there is dropdown menu named "New" with which you can create a Jupyter notebook file ("Python"), a "Text File", or open a "Terminal".   


### Setting up on Jupyter Hub

So why is it actually possible to open a terminal window? This is because upon login, a new Ubuntu user account with the username `jupyter-{tumid}` is created for you on our server. You can therefore use this terminal to manage your file system on the Jupyter hub, e.g., create new folders, and, most importantly, get the course material.

We have installed `git` and `conda` for all accounts already. So, all you have to do is to configure `git`, i.e., connect it to you `github` account, clone the course github repository with all the course material, and then install all the required packages using `conda`. In particular, you need to (in the terminal on your jupyter hub account):

1.  Follow steps 2 - 4 from [Cloning this repository](#cloning-this-repository)

2. Go back to your main jupyter hub browser tab and acknowledge that there is a new folder `lsmlsda` holding all the current course material.

3. Back in the terminal window follow the instructions in [Installing required packages](#installing-required-packages). That is, install the conda environment via
    ```
    conda env create -f environment.yml
    ```
    You have to confirm the installation of all the packages and wait a bit...

4. Now activate the environment via
    ```
    conda activate lsmlsda
    ```

5. Finally, we have to initialize `conda` and tell the Jupyter hub about the new conda environment such that it can be used in all notebook. To this end, execute
    ```
    conda init
    ipython kernel install --user --name lsmlsda
    ```
    to initialize conda and register the new environment. Then close the terminal window, log out of Jupyter hub and log in again.

6. Now you should be able to open any project-related `jupyter notebook` or python file and execute them on the server.

7. If you have any questions let us know.
