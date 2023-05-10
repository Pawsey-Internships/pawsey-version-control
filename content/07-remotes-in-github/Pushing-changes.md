+++
title = "c. Pushing Changes"
weight = 2
chapter = false
+++

## Push local changes to a remote

Now that authentication is setup, we can return to the remote.  This command will push the changes from
our local repository to the repository on GitHub:

```Bash
$ git push origin main
```


```
Enumerating objects: 16, done.
Counting objects: 100% (16/16), done.
Delta compression using up to 8 threads.
Compressing objects: 100% (11/11), done.
Writing objects: 100% (16/16), 1.45 KiB | 372.00 KiB/s, done.
Total 16 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), done.
To https://github.com/vlad/planets.git
 * [new branch]      main - main
```


If you set a passphrase for your SSH key you will be prompted for it here otherwise it will push with no issues.

{{% notice note %}}
## Proxy

 If the network you are connected to uses a proxy, there is a chance that your
 last command failed with "Could not resolve hostname" as the error message. To
 solve this issue, you need to tell Git about the proxy:

 ```Bash
 $ git config --global http.proxy http://user:password@proxy.url
 $ git config --global https.proxy https://user:password@proxy.url
 ```
 

 When you connect to another network that doesn't use a proxy, you will need to
 tell Git to disable the proxy using:

 ```Bash
 $ git config --global --unset http.proxy
 $ git config --global --unset https.proxy
 ```
{{% /notice %}} 

{{% notice note %}}
## Password Managers

 If your operating system has a password manager configured, `git push` will
 try to use it when it needs your username and password.  For example, this
 is the default behavior for Git Bash on Windows. If you want to type your
 username and password at the terminal instead of using a password manager,
 type:

 ```Bash
 $ unset SSH_ASKPASS
 ```
 

 in the terminal, before you run `git push`.  Despite the name, [Git uses
 `SSH_ASKPASS` for all credential
 entry](https://git-scm.com/docs/gitcredentials#_requesting_credentials), so
 you may want to unset `SSH_ASKPASS` whether you are using Git via SSH or
 https.

 You may also want to add `unset SSH_ASKPASS` at the end of your `~/.bashrc`
 to make Git default to using the terminal for usernames and passwords.
{{% /notice %}}

Our local and remote repositories are now in this state:

![GitHub Repository After First Push](images/github-repo-after-first-push.svg)

{{% notice note %}}
## The '-u' Flag

 You may see a `-u` option used with `git push` in some documentation.  This
 option is synonymous with the `--set-upstream-to` option for the `git branch`
 command, and is used to associate the current branch with a remote branch so
 that the `git pull` command can be used without any arguments. To do this,
 simply use `git push -u origin main` once the remote has been set up.
{{% /notice %}}

We can pull changes from the remote repository to the local one as well:

```Bash
$ git pull origin main
```


```
From https://github.com/vlad/planets
 * branch            main     - FETCH_HEAD
Already up-to-date.
```


Pulling has no effect in this case because the two repositories are already
synchronized.  If someone else had pushed some changes to the repository on
GitHub, though, this command would download them to our local repository.
