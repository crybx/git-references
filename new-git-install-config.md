## CONFIG SETUP FOR A NEW INSTALLATION OF GIT

### check current user information

```
git config --global user.name     
git config --global user.email
```

### set current user information

```
git config --global user.name "Username"     
git config --global user.email "your.email@example.com"
```

for me:

```
git config --global user.name "crybx"     
git config --global user.email "crybx@users.noreply.github.com"
```

### default settings I like

```
git config --global pull.rebase true
git config --global fetch.prune true
git config --global diff.colorMoved zebra
```

These are:

- Pull with Rebase
- Prune on Fetch
- Differentiate Moved Lines - changed colors in diff for "moves"

### check line endings setting

`git config core.autocrlf`

### set line endings setting

`git config core.autocrlf <true/false>`

- false means don't convert anything
- true is what you want if all work will be done on Windows

I've read so much about git and line endings, and I still get frustrated. I don't like any of the options. 

### generate an SSH key

On pc, per GitHub's instructions (use the email you would use to log in to GitHub):

`ssh-keygen -t ed25519 -C "your_email@example.com"`

> Note: If you are using a legacy system that doesn't support the Ed25519 algorithm, use:
> 
> `ssh-keygen -t rsa -b 4096 -C "your.email@example.com"`

on pc:

`ssh-keygen -t rsa -C "your.email@example.com"`

add key to server (on a Linux box serving as a Git server):  

`cat ~/.ssh/id_rsa.pub | ssh user@hostname 'cat >> ~/.ssh/authorized_keys'`

### see all your config values and where they are set

`git config --list --show-origin`
