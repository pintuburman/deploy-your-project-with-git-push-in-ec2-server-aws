# Deploy your project with git push in ec2 server aws

Creating the “Bare” Git Repositories
Once you’ve decided which directory will house your remote repositories, you can start creating repositories first as directories ending with a .git extension. The extension is important, as it distinguishes the directories containing Git repositories from regular directories.

For example, to create a repository called “website,” create a directory like so:

```html
mkdir website.git
```

Then, enter the directory with the cd command:
```html
cd website.git
```

Once inside the directory, create a “bare” Git repository:

```html
git init --bare
```

Now, when you add website.git as a remote repository (as you’ll see how below) Git will be able to recognize it.

Creating the --bare git repository basically means you are telling Git, “There is nothing in this repository yet, but I want this directory (website.git) to function as a remote repository.


Then, enter the directory with the cd command:
```html
cd hooks
```

Then, rename the post.update.sample to post.update and remove all content to 

```html
GIT_WORK_TREE=/path/to/server/project/folder/ git checkout -f
```


Add Your Remote Repository
So far, you have created a git user account, a bare repository in the directory of your choice, and you have SSH key authentication set up for the git user.

Now, you just need to make your local Git installation aware of the new repository:

```html
git remote add production ubuntu@[server_ip_address]:/path/to/website.git
```

Let us break this command a little bit.

The git remote add command initiates the addition of a repository. The “origin” part names the new repository. You can put any name you want, you don’t have to use “origin,” but it is merely a conventional naming scheme.

The rest of the command specifies the precise server file path to the bare Git repository you created.

The final step is to push your project to the new repository. For example, if you are pushing the “master” branch, the command will look like this:

```html
git push -f production master
```


# ON SERVER SIDE FULL EXAMPLE
```
$ cd /var/www/git
$ mkdir website.git
$ cd website.git
$ git init --bare
$ cd hooks
$ cp post.update.sample post.update
$ vi post.update

GIT_WORK_TREE=/path/to/server/project/folder git checkout -f

save the above content in post.update
```


# ON CLIENT SIDE FULL EXAMPLE
```
# on John's computer
$ cd myproject
$ git init
$ git add .
$ git commit -m 'Initial commit'
$ git remote add production ubuntu@[server_ip_address]:/path/to/website.git
$ git push -f production master
```



That’s it! You now know how to create your own Git repository on a private server.



#ssh setupp in windows machine

![alt text](https://github.com/pintuburman/deploy-your-project-with-git-push-in-ec2-server-aws/blob/main/ssh_config_file.jpg)


```
Host *
     ForwardAgent no
     ForwardX11 no
     ForwardX11Trusted yes
     Port 22
     Protocol 2
     ServerAliveInterval 60
     ServerAliveCountMax 30
     AddKeysToAgent yes

Host [server_ip_address_without_brackets]
  HostName [server_ip_address_without_brackets]
  User [server_user_example_ubuntu]
  IdentityFile ~/.ssh/[file_name_which_contains_ssh_key]
```




