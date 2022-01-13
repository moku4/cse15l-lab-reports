WEEK 2
# Lab Report 1 - Remote Access

Hello Everyone, my name is Uri and today I'll demo how we can all access and log into our `ieng6` accounts.

## Installing VSCode

The first step sommence our journey is to download [VSCode](https://code.visualstudio.com/) with the link provided. Please make sure to have a device that meets the requirements for installment. Depending on the device, slect the appropriate install option. In my case, I'll downloading the Windows version. Once installed, open VSCode. 



## Remotely Connecting

Windows users have to make  sure to install `OpenSSH` on their PC before proceeding. To [install OpenSSH](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse) on your device make sure to check out the link provided. Make sure you know youre account name for the course you're taking. Use this link to access your account:

[Accessing account](https://sdacs.ucsd.edu/~icc/index.php)

Once VSCode is opened, open a terminal by clicking on the `Terminal` tab on the toolbar at the very top and clicking on `New Terminal`. Next, enter the following into the command line and remember to replace `abc`.

```
$ ssh cs15lwi22abc@ieng6.ucsd.edu
```

On the first attempt a message may show up saying, "`The authenticity of host...`" just type yes and press enter and enter your password. Congratulations, you are finlly conencted and your screen shoud look like this:

## Trying Some Commands

There are a lot of commands to play around with on the remote computer. Here are some commands that might be helpful in the future and what they do. 

* `cd` - Change directory.
* `ls` - Shows directory contents.
* `mkdir` - Create a new directory folder.
* `pwd` - Shows current directory
* `cp` - Copy a file or folder.
* `cat` - Shows contents of a file.
* `exit` - Logs out of account.

## Moving Files with scp

We can use `scp` to move files back and forth between computers. Make sure to be logged off of your account to proceed with the next steps. 

Create a java file on your computer. Make sure you can compile and run it with no problems. I'll be using `WhereAmI.java` On a terminal, run your file using javac and java. Next, run the following command from the directory the file is in:

```
$ scp WhereAmI.java cs15lwi22abc@ieng6.ucsd.edu:~/
```
Enter your password when asked. You can log into your remote account and use `ls` to make sure your files are in your home directory. 

## Setting an SSH Key

Set up an SSH Key for faster programming by running the following lines in your `Terminal`:

```
$ ssh-keygen

$ /Users/<your computer username>/.ssh/id_rsa

$ (Empty for no passphrase twice)
```

Your screen should look like this:

If you're using windows make sure follow the `ssh-add` steps from this website to complete the step, [https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement#user-key-generation](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement#user-key-generation).

Once that step is done, two new files have been created and our system. Now, we need to copy the public key to the `.ssh` directory of our accounts. Run the follwing commands:

```
$ ssh cs15lwi22abc@ieng6.ucsd.edu

$ mkdir .ssh

$ exit

$ scp /Users/<Your computer username>/.ssh/id_rsa.pub cs15lwi22@ieng6.ucsd.edu:~/.ssh/authorized_keys
```

## Optimizing Remote Running

There are sveral ways to make our programming faster on the terminals. One way would be to add a command after an `ssh` command to run it directly on the remote server. Semicolons also allow for multiple commands to run on one line. Here are some examples:

```
$ ssh cs15lwi22@ieng6.ucsd.edu "ls"

$ cp WhereAmI.java; javac WhereAmI.java; java WhereAmI
```
