# Only one notebook in this tutorial

 1. `scientific-python-tutorial.ipynb`: a whirlwind tour of all the Python packages available in CMSSW

## Getting started

We will use Jupyter to present these tutorials, only because it is a convenient interface to Python. Everything that we will present can be performed the normal way, by editing scripts and running them from the command line (with `python -i` in your terminal). However, a notebook interface lets you interact with the process and retry steps, which is good for learning.

Before proceeding with the next step, which will open an ssh tunnel to the lpc cluster, please review the content of your `~/.ssh/config` file on your system by executing:

    cat ~/.ssh/config

In case the file does already contain the following lines, consider adding them (opening the file with your favorite editor):

    Host cmslpc*.fnal.gov
        StrictHostKeyChecking no
        UserKnownHostsFile /dev/null

Please note this is not safe in general, so make sure you have the `Host cmslpc*.fnal.gov` line in there!

When you log into cmslpc, add a `-L` option to your ssh command:

    ssh -L localhost:8888:localhost:8888 <YOUR USERNAME>@cmslpc-sl6.fnal.gov

On cmslpc, if you do not already have one, create a HATS directory in your `~/nobackup` directory (which has a more generous quota than your home directory):


    mkdir ~/nobackup/HATS

move to it:

    cd ~/nobackup/HATS

and create a CMSSW directory as usual (version 9 and above):

for bash:

    source /cvmfs/cms.cern.ch/cmsset_default.sh

for cshell:

    source /cvmfs/cms.cern.ch/cmsset_default.csh
    
for bash:

    export SCRAM_ARCH=slc6_amd64_gcc530
    
for cshell:

    setenv SCRAM_ARCH slc6_amd64_gcc530
    
either way:
    
    cmsrel CMSSW_9_0_1
    cd CMSSW_9_0_1/src
    cmsenv

and then clone this repository:

    git clone https://github.com/FNALLPC/scientific-python-hats.git
    cd scientific-python-hats

Now start Jupyter with this command:

    jupyter notebook --no-browser --port=8888 --ip localhost

After a pause (while cmslpc loads the necessary libraries for the first time) you should see a message like the following:

    [I 08:22:45.871 NotebookApp] Serving notebooks from local directory: /uscms_data/d2/pivarski/CMSSW_9_0_0_pre6/src
    [I 08:22:45.871 NotebookApp] 0 active kernels 
    [I 08:22:45.871 NotebookApp] The Jupyter Notebook is running at: http://localhost:8888/?token=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
    [I 08:22:45.871 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
    [C 08:22:45.873 NotebookApp] 
        
        Copy/paste this URL into your browser when you connect for the first time,
        to login with a token:
            http://localhost:8888/?token=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

Copy/paste the URL it gives you into your web browser and from now on, all interactions with Python and your user account will be through the browser. The `-L` option we passed to ssh is forwarding Jupyter's web traffic through SSH, so your account is safe, even if you access it from home.

Jupyter and all the other Python libraries we will be studying are bundled in CMSSW. For these exercises, there is no need to install anything else.

Within Jupyter, click on the `scientific-python-ecosystem` directory and then `scientific-python-tutorial.ipynb`. You are now ready to start the tutorial.
