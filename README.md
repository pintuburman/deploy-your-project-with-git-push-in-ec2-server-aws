# git-setup-in-ec2-server-aws

Creating the “Bare” Git Repositories
Once you’ve decided which directory will house your remote repositories, you can start creating repositories first as directories ending with a .git extension. The extension is important, as it distinguishes the directories containing Git repositories from regular directories.

For example, to create a repository called “website,” create a directory like so:

# mkdir website.git

Then, enter the directory with the cd command:

# cd website.git

Once inside the directory, create a “bare” Git repository:

# git init --bare

Now, when you add website.git as a remote repository (as you’ll see how below) Git will be able to recognize it.

Creating the --bare git repository basically means you are telling Git, “There is nothing in this repository yet, but I want this directory (website.git) to function as a remote repository.

Add Your Remote Repository
So far, you have created a git user account, a bare repository in the directory of your choice, and you have SSH key authentication set up for the git user.

Now, you just need to make your local Git installation aware of the new repository:

# git remote add origin git@server:/path/to/website.git

Let us break this command a little bit.

The git remote add command initiates the addition of a repository. The “origin” part names the new repository. You can put any name you want, you don’t have to use “origin,” but it is merely a conventional naming scheme.

The rest of the command specifies the precise server file path to the bare Git repository you created.

The final step is to push your project to the new repository. For example, if you are pushing the “master” branch, the command will look like this:

# git push origin master

That’s it! You now know how to create your own Git repository on a private server.
