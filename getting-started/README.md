# Getting started


Welcome to Minifolio! If you haven't already deployed your instance, make sure to [check out the deploy instructions](/deploy) first.


When you first create your instance, it will walk you through creating an account, then setting up your data.


## Creating an account {#account}


1. Enter a username. For security, you may wish to avoid common usernames such as `admin`.
2. Create a unique and secure password. It must contain at least:
    * A lowercase letter
    * An uppercase letter
    * A number
    * A symbol
    * 8 characters
3. Repeat this password


## Setting up your data {#data}


To get started immediately, you can choose the "I don't want to use git" option at the bottom of the page. Otherwise, you will need to set up some of the following.


### Creating a data repository


If you don't have a data repository already, you should [create one](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository).


Make sure your repository is entirely empty. Don't generate a README file or create a license yet, as Minifolio currently cannot handle non-empty repositories unless they have existing portfolio data.


### Setting up SSH access


If you want to be able to run git operations from the admin panel, you will need to set up an SSH key or use your system's SSH if running outside of Docker. Currently, Minifolio does not support password authentication for Git operations.


To generate a new SSH key:


1. Click "Generate SSH key"
2. Copy the public key that is generated.
3. Add this SSH to your account on your desired Git remote, or set it up so it can only be used to access your repository.


To use an existing SSH key:


1. Ensure that this SSH key is passed through to your Docker container if you have deployed Minifolio within one.
2. Enter the path to the private key into Minifolio, then choose "Set SSH key path"
3. Minifolio should display the public key if the operation was a success.


### Cloning your data repository


1. Paste the clone URL of your data repository. This should be an SSH URL if you intend to perform Git operations from the Minifolio admin panel.
2. Enter your desired branch name, or leave empty to use the primary branch (eg `main`).
3. Press the "Let's go" button, and Minifolio will clone and set up your data repository for you.

