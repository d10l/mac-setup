# Git and GitHub

What's a developer without [Git](http://git-scm.com/)? To install, run:

    $ brew install git

When done, to test that it installed properly you can run:

    $ git --version

And `which git` should output `/usr/local/bin/git`.

Next, we'll define your Git user (should be the same name and email you use for
[GitHub](https://github.com/)):

```sh
$ git config --global user.name "Your Name Here"
$ git config --global user.email "your_email@youremail.com"
```

They will get added to your `.gitconfig` file.

To push code to your GitHub repositories, we're going to use the recommended
HTTPS method (versus SSH). To prevent `git` from asking for your username and
password every time you push a commit you can cache your credentials by running
the following command, as described in the
[instructions](https://help.github.com/articles/caching-your-github-password-in-git/).

    $ git config --global credential.helper osxkeychain

## SSH Config for GitHub

The instructions below are referenced from [the official
documentation](https://help.github.com/articles/generating-ssh-keys).

### Check for existing SSH keys

First, we need to check for existing SSH keys on your computer. We do this by
running:

```sh
$ ls -al ~/.ssh
# Lists the files in your .ssh directory, if they exist
```

Check the directory listing to see if you have files named either `id_rsa.pub`
or `id_dsa.pub`. If you don't have either of those files then read on,
otherwise skip the next section.

### Generate a new SSH key

If you don't have an SSH key you need to generate one. To do that you need to
run the commands below, and make sure to substitute the placeholder with your
email. The default settings are preferred, so when you're asked to "enter a
file in which to save the key,"" just press Enter to continue.

```sh
$ ssh-keygen -t rsa -C "your_email@example.com"
# Creates a new ssh key, using the provided email as a label
```

### Add your SSH key to the ssh-agent

Run the following commands to add your SSH key to the `ssh-agent`.

```sh
$ eval "$(ssh-agent -s)"
```

If you're running macOS Sierra 10.12.2 or later, you will need to modify your
`~/.ssh/config` file to automatically load keys into the ssh-agent and store
passphrases in your keychain:

```keychain
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
```

No matter what operating system version you run you need to run this command to
complete this step:

```sh
$ ssh-add -K ~/.ssh/id_rsa
```

### Adding a new SSH key to your GitHub account

The last step is to let GitHub know about your SSH key. Run this command to copy your key to your clipboard:

```sh
$ pbcopy < ~/.ssh/id_rsa.pub
```

Then go to GitHub and [input your new SSH
key](https://github.com/settings/ssh/new). Paste your key in the "Key" textbox
and pick a name that represents the computer you're currently using.

## Setup a template for git to prevent checking in credentials

[Source](https://seesparkbox.com/foundry/git_secrets)

1. Install `git secrets`

```sh
brew install git-secrets
```

2. Make a directory for the template:

   ```text
   mkdir ~/.git-template
   ```

3. Install the hooks in the template directory:

   ```text
   git secrets --install ~/.git-template
   ```

4. Tell git to use it:

   ```text
   git config --global init.templateDir '~/.git-template'
   ```

5. Install AWS patterns globally to be prevented to be checked in to git:

   ```text
   git secrets --register-aws --global
   ```

6. Check the list of secrets `git secrets` will scan for:

   ```text
   git secrets --list
   ```

It should return something like:

```text
secrets.providers git secrets --aws-provider
secrets.patterns [A-Z0-9]{20}
secrets.patterns ("|')?(AWS|aws|Aws)?_?(SECRET|secret|Secret)?_?(ACCESS|access|Access)?_?(KEY|key|Key)("|')?\s*(:|=>|=)\s*("|')?[A-Za-z0-9/\+=]{40}("|')?
secrets.patterns ("|')?(AWS|aws|Aws)?_?(ACCOUNT|account|Account)_?(ID|id|Id)?("|')?\s*(:|=>|=)\s*("|')?[0-9]{4}\-?[0-9]{4}\-?[0-9]{4}("|')?
secrets.allowed AKIAIOSFODNN7EXAMPLE
secrets.allowed wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
```

Now every time you run `git init` or `git clone`, your hooks will be copied into the `.git` directory of your freshly created repo. If you don’t want to set the template globally, you can use it as needed with `git init --template ’~/.git-template’`.

That covers new repo creation, and cloning, but we haven’t addressed the problem of _existing repos that weren’t created with the template_. Here we have a couple options:

`git init` is a non-destructive operation, so feel free to run it in existing repos. It’s safe, and will retroactively apply the template you specify.

OR

If you want to go “all in” and ensure that every repo has the proper hooks, here’s a [script](https://gist.github.com/iAmNathanJ/0ae03dcb08ba222d36346b138e83bfdf) that will recursively walk a directory, such as `~/Projects` and run `git secrets --install` in all repos.

## Git Best Pratices

Read [Single Branch Development with Git](https://medium.com/learn-git-today/single-branch-development-with-git-f72a052446cf) and [global commit messages](https://eidson.info/post/using-conventional-commit-messages-globally) following the [angular commit message guidelines](https://github.com/angular/angular/blob/master/CONTRIBUTING.md#-commit-message-guidelines).

### [Github CLI](https://hub.github.com/)

Install:

```bash
brew install hub
# https://hub.github.com/hub.1.html
git config --global hub.protocol https
```