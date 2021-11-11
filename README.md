# githubcommit

githubcommit is a jupyter notebook extension enabling users push ipython notebooks to a git repo.
The git button gets displayed in the notebook toolbar. After saving any notebook
the user can push notebook to pre-specified git repository. There are few
environment variables that must be exported. Currently this extension supports
commits to a single github repo defined in environment variable but in the long
run need help to modify this extension allowing user to select his repo and branch.

## Installation

You can currently install this directly from git:

```
pip install git+https://github.com/engineerali2009/GitHubWithJupyter.git
jupyter serverextension enable --py githubcommit
jupyter nbextension install --py githubcommit --user
```

To enable this extension for all notebooks:

```
jupyter nbextension enable githubcommit --user --py
```

## Steps

* Install package using above commands
* If you’re using Macos, that command would be:

brew install git

* You probably already have git installed, but on the off-chance you don’t, issue the following command for linux:

sudo apt-get install git -y

* For Gui Installing  git-gui
If you would like to install git-gui and gitk, git's commit GUI and interactive history browser, you can do so using homebrew
$ brew install git-gui
* Generate SSH keys
You’ll also need SSH keys (so you can clone the necessary repository). For this, run the command:

ssh-keygen

* Make sure to accept the defaults and give the key a unique and strong password.

*Once you’ve generated the key, view the public key with the command:

 cat ~/.ssh/Your_Key_Name.pub
 
* Copy the contents of that key and head over to your GitHub account. Go to Settings > SSH and GPG keys and click New SSH Key. In the resulting window, paste the SSH key you just generated, give it a name, and click Add SSH Key.

* Generating a new SSH key

* Open Terminal.
* Paste the text below, substituting in your GitHub email address.
$ ssh-keygen -o"
* Navigate and copy your key using 
* 
* cat ~/.ssh/Your_Public_Key_Name.pub

* Add your key to keychain

 ssh-add -K ~/.ssh/Your_Public_Key

* Clone the Repository
* We need to clone the extension repository, with the command:

git clone git@github.com:engineerali2009/GitHubWithJupyter.git

* You will be asked for the password for your SSH key you just created. When this finishes, a new directory will be created, named githubcommit.

* With the repository cloned, let’s make sure Git knows who we are. Issue the following two command:
 git config --global user.name "Your Name"
 git config --global user.email "Your Email"

 git config --get user.name 
 git config --get user.email 

* Where EMAIL is your email address and NAME is your name.
* Create a GitHub Access Token
* Next, you need to create a GitHub access token. Go to your GitHub account and then to Settings > Developer Settings > Personal Access Tokens. Click Generate New Token and * then, in the resulting window, give it a name and check the boxes for repo and write:packages. Scroll to the bottom and click Generate token. You’ll then need to copy * that access token to your clipboard.


 
* Configure the Extension
* Change into the YourRepoName folder with the command:

cd YourRepoName

* Open the env.sh configuration file with the command:

nano env.sh

* In that file, you must configure the following section:


* Create Git repo where notebooks will be pushed if not already exists and clone it in your `GIT_PARENT_DIR`
* Clone this repo as well in your `GIT_PARENT_DIR` directory
* Replace the values in env.sh present in this repo itself
* Run the command - source ~/YourRepoName/env.sh
* Configure ssh key (present in ~/.ssh/id_rsa.pub or specified location) in github account
* Run jupyter notebook from within your repo directory






## Example git configuration
export GIT_PARENT_DIR=~ <br />
export GIT_REPO_NAME=GitHubWithJupyter <br />
export GIT_BRANCH_NAME=master <br />
export GIT_USER=UserName <br />
export GIT_EMAIL=Your_Mail <br />
export GITHUB_ACCESS_TOKEN=#access-token from github developer settings <br />
export GIT_USER_UPSTREAM=engineerali2009 <br />

where:

REPONAME is the name of a GitHub repository you’ll use for this.
BRANCH is the repository branch (probably “main”)
USERNAME is your GitHub username
EMAIL is the email address associated with your GitHub account
ATOKEN is the access token you just created.
Save and close the file.



You will be prompted for your SSH key password. Once you’ve done that, the repository you configured in the env.sh file will clone to your local drive (in your home directory). When that completes, change into the new directory that cloned from your GitHub repository (in my case it was named newstack).

From within that directory, launch the notebook with the command:

jupyter notebook --ip 0.0.0.0
If it doesnt work try 
--ip 127.0.0.1

Your notebook should open to reveal all of the files from your GitHub repository 

If you create a new file or open one, you’ll now see a GitHub logo in your notebook 

Here’s where the caveat comes into play. You should be able to click that button and then commit any new code to the connected GitHub repository. 
## Credits

Thanks to https://github.com/Lab41/sunny-side-up for laying the foundation of this extension.

Thanks to https://github.com/sat28 for support.

