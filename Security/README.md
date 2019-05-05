# Security and Safety

A development machine should be secured against threads as well as any other machine \(or even _especially_ a development machine\). Therefore we will setup

* secure system settings
* a virus scanner
* a firewall
* disk encryption

## Secure System Settings

Check out [Stronghold](https://www.github.com/alichtman/stronghold) for the easiest way to configure macOS security settings from the terminal.

## Virus Scanner

Head over to [Avira](https://www.avira.com/), download and install their latest free package.

## Firewall

This one is a bit controversial. If you do not install software which allows network access of any kind, skip it. If you run potentially vulnerable software you don't want to be accessed from other machines, consider turning the built-in firewall on. This particularly applies if you develop network software.

To turn the built-in firewall on:

1. Choose Apple menu \(\) &gt; System Preferences, then click Security & Privacy.
2. Click the Firewall tab.
3. Click the Lock button, then enter an administrator name and password.
4. Click Turn On Firewall.
5. Click Firewall Options.
6. Uncheck 'Automatically allow signed software to receive incoming connections'.

The last step disables automatic access for software from the App Store. From now on you can either add \(dis\)allowed programs to the list within the Firewall Options or just click on Allow\/Deny, if you get a popup asking you if a specific software may be accessed.

## Disk Encryption

Another controversial point. If you have a desktop machine in a secured building, you probably do not need disk encryption. If you travel a lot and take your notebook with you \(including all your source codes\), you might consider travelling with disk encryption enabled.

The following steps were taken from the [official apple support page](https://support.apple.com/en-us/HT204837) on this:

1. Choose Apple menu \(\) &gt; System Preferences, then click Security & Privacy.
2. Click the FileVault tab.
3. Click the Lock button, then enter an administrator name and password.
4. Click Turn On FileVault.
5. Follow the instructions. In my opinion you should create a local and offline possibility to disable encryption, when you are asked how to regain access in case of anything.

## Config & Keybase

Store your secret configuration files using [keybase.io](https://keybase.io/) in a shared but end to end encrypted folder, and git repositories.

1. Install the [Keybase app](https://keybase.io/docs/the_app/install_macos)  `brew cask install keybase`
2. Install the GPG suite `brew cask install gpg-suite`
3. If you don't have a GPG key already create a new GPG key `keybase pgp gen` otherwise just import your existing key with `keybase pgp select`.

### Sign git commits

1. Grab the public key using `keybase pgp export`, then feed it into GitHub described [here](https://help.github.com/en/articles/adding-a-new-gpg-key-to-your-github-account).
2. `git config --global user.signingkey <my_key_ID>` – Tell my local git to use my GPG key for signing ([how to get my key id](https://help.github.com/en/articles/telling-git-about-your-signing-key))
3. `git config --global commit.gpgsign true` – Enable GPG commit signing
4. What you end up with are commits that have the “Verified” label in GitHub, which is an affirmation that I was actually the one who made those commits.

### Share secrets config files with devops pipeline

1. create a seperate account & generate a [paperkey](https://keybase.io/docs/command_line/basics) for this account with `keybase paperkey`. with this paper key you can now login from your cicd pipeline using your username (not email!) and the paperkey.
   1. `keybase oneshot  --paperkey xxx -u username` for more infos do `man keybase oneshot` or look at an [example](https://gitlab.com/open-source-devex/containers/keybase/blob/master/container/build-docker-entrypoint.sh)
   2. Publish the relevant crednetials files to `/keybase/private/dennisseidel,cicdbotname` or to your `teams` folder.

## LastPass

## Securely store your keys and secrets

You don't want to store your secrets in plain text in a file like `.rshrc`  therefore you can use lpass cli \[[github](https://github.com/lastpass/lastpass-cli) / [documentation](https://helpdesk.lastpass.com/lastpass-command-line-application/)\] and store your secrets in your osx keychain and access them only by reference.

### Installation

```bash
brew install lastpass-cli --with-pinentry
```

#### Set variables in lastpass

Just create a secret note within lastpass:

<img src="./add-secret-to-lastpass.png" width="80%">

#### Login to lpass in the command line

```bash
# login to lastpass# check first if I am allready loggedin and finded the "access-token" folder if [[ $(lpass ls) != *"access-token"* ]]; thenlpass login your@email.comfi
```

#### Set environment variable \(e.g. key\_id \(username\) and secret\(password\)

```bash
export AWS_ACCESS_KEY_ID=$(lpass show aws-serverless-devops --username)
export AWS_SECRET_ACCESS_KEY=$(lpass show aws-serverless-devops --password)
```

### Accessing files in lpass

```text
lpass show xxx-dev-gcp --attach att-7942806310206912061-56085
```

### Setup an ecrypted folder and sync with google drive

```text
/Users/den/Desktop/secret/xxx/key.json
lock-secret-files
unlock-secret-files
```