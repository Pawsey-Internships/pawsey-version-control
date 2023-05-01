+++
title = "b. Authentication"
weight = 2
chapter = false
+++

Before Dracula can connect to a remote repository, he needs to set up a way for his computer to authenticate with GitHub so it knows it’s him trying to connect to his remote repository.

We are going to set up the method that is commonly used by many different services to authenticate access on the command line.  This method is called Secure Shell Protocol (SSH).  SSH is a cryptographic network protocol that allows secure communication between computers using an otherwise insecure network.

SSH uses what is called a key pair. This is two keys that work together to validate access. One key is publicly known and called the public key, and the other key called the private key is kept private. Very descriptive names.

You can think of the public key as a padlock, and only you have the key (the private key) to open it. You use the public key where you want a secure method of communication, such as your GitHub account.  You give this padlock, or public key, to GitHub and say “lock the communications to my account with this so that only computers that have my private key can unlock communications and send git commands as my GitHub account.”

What we will do now is the minimum required to set up the SSH keys and add the public key to a GitHub account.

{{% notice note %}}
## Advanced SSH
 A supplemental episode in this lesson discusses SSH and key pairs in more depth and detail.
{{% /notice %}}

{{% notice note %}}
## A note on PAT's

 Personal access tokens (PAT) are an alternative to SSH keys intended solely for use as authentication for GitHub
 remote repositories. As of Augst 2021 GitHub will no longer accept password based authentication so if you wish to
 use GitHub without SSH you must create one.
 Unlike SSH keys they are used in places where a password would normally be used such as the git command line, GitHub
 cli or IDE git integration.
 They look like this:
 ```
 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
 ```
 
 As such they are normally stored with some kind of credential manager. On MacOS this will be the Keychain Access app
 and on windows or Linux it will be the Git Credential Manager (GCM). See [the github instructions](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) for how to create an use a PAT.
{{% /notice %}}


  * [ ] The first thing we are going to do is check if this has already been done on the computer you’re on.  Because generally speaking, this setup only needs to happen once and then you can forget about it.

{{% notice note %}}
## Keeping your keys secure
 You shouldn't really forget about your SSH keys, since they keep your account secure. It’s good
  practice to audit your secure shell keys every so often. Especially if you are using multiple
  computers to access your account.
{{% /notice %}}

We will run the list command to check what key pairs already exist on your computer.

```Bash
ls -al ~/.ssh
```


Your output is going to look a little different depending on whether or not SSH has ever been set up on the computer you are using.

Dracula has not set up SSH on his computer, so his output is

```
ls: cannot access '/c/Users/Vlad Dracula/.ssh': No such file or directory
```


If SSH has been set up on the computer you're using, the public and private key pairs will be listed. The file names are either `id_ed25519`/`id_ed25519.pub` or `id_rsa`/`id_rsa.pub` depending on how the key pairs were set up.

Since they don’t exist on Dracula’s computer, he uses this command to create them:

```
$ ssh-keygen -t ed25519 -C "vlad@tran.sylvan.ia"
```

{{% notice note %}}
## Legacy Systems

 Ed25519 is an [EdDSA](https://en.wikipedia.org/wiki/EdDSA) scheme with small fixed size keys introduced in
 OpenSSH 6.5. However because it is a rather new algorithm its adoption is not yet universal.
 If you are using a legacy system that doesn't support the Ed25519 algorithm, use:
 ```Bash
 $ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
 ```
 
 as it will generate an RSA key of similar complexity.
{{% /notice %}}

{{% notice note %}}
## Windows

 To generate an SSH key on windows you will need the Windows Subsystem for Linux (WSL) installed.
 This also means that authentication to remote repositories will need to be done in the WSL shell
 and it will be more convenient to use the WSL filesystem.
{{% /notice %}}

```
Generating public/private ed25519 key pair.
Enter file in which to save the key (/c/Users/Vlad Dracula/.ssh/id_ed25519):
```


We want to use the default file, so just press <kbdEnter</kbd.

```
Created directory '/c/Users/Vlad Dracula/.ssh'.
Enter passphrase (empty for no passphrase):
```


Now, it is prompting Dracula for a passphrase.  Since he is using his lab’s laptop that other people sometimes have access to, he wants to create a passphrase.  Be sure to use something memorable or save your passphrase somewhere, as there is no "reset my password" option. 

```
Enter same passphrase again:
```


After entering the same passphrase a second time, we receive the confirmation

```
Your identification has been saved in /c/Users/Vlad Dracula/.ssh/id_ed25519
Your public key has been saved in /c/Users/Vlad Dracula/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:SMSPIStNyA00KPxuYu94KpZgRAYjgt9g4BA4kFy3g1o vlad@tran.sylvan.ia
The key's randomart image is:
+--[ED25519 256]--+
|^B== o.          |
|%*=.*.+          |
|+=.E =.+         |
| .=.+.o..        |
|....  . S        |
|.+ o             |
|+ =              |
|.o.o             |
|oo+.             |
+----[SHA256]-----+
```


The "identification" is actually the private key. You should never share it.  The public key is appropriately named.  The "key fingerprint" 
is a shorter version of a public key.

Now that we have generated the SSH keys, we will find the SSH files when we check.

```Bash
ls -al ~/.ssh
```


```
drwxr-xr-x 1 Vlad Dracula 197121   0 Jul 16 14:48 ./
drwxr-xr-x 1 Vlad Dracula 197121   0 Jul 16 14:48 ../
-rw-r--r-- 1 Vlad Dracula 197121 419 Jul 16 14:48 id_ed25519
-rw-r--r-- 1 Vlad Dracula 197121 106 Jul 16 14:48 id_ed25519.pub
```


Now we run the command to check if GitHub can read our authentication.  

```Bash
ssh -T git@github.com
```



```
The authenticity of host 'github.com (192.30.255.112)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? y
Please type 'yes', 'no' or the fingerprint: yes
Warning: Permanently added 'github.com' (RSA) to the list of known hosts.
git@github.com: Permission denied (publickey).
```


Right, we forgot that we need to give GitHub our public key!  

First, we need to copy the public key.  Be sure to include the `.pub` at the end, otherwise you’re looking at the private key. 

```Bash
cat ~/.ssh/id_ed25519.pub
```


```
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIDmRA3d51X0uu9wXek559gfn6UFNF69yZjChyBIU2qKI vlad@tran.sylvan.ia
```


Now, going to GitHub.com, click on your profile icon in the top right corner to get the drop-down menu.  Click "Settings," then on the 
settings page, click "SSH and GPG keys," on the left side "Account settings" menu.  Click the "New SSH key" button on the right side. Now, 
you can add the title (Dracula uses the title "Vlad's Lab Laptop" so he can remember where the original key pair
files are located), paste your SSH key into the field, and click the "Add SSH key" to complete the setup.

Now that we’ve set that up, let’s check our authentication again from the command line. 
```
$ ssh -T git@github.com
```


```
Hi Vlad! You've successfully authenticated, but GitHub does not provide shell access.
```


Note: To achieve the above output, you may be prompted to enter your previously created passphrase. If so, type in the passphrase and press enter.
