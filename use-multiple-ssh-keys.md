[< Git References](README.md)

# USE MULTIPLE GIT IDENTITIES ON ONE MACHINE

## manually switch ssh key

Go to your `.ssh/` directory.

- `id_ed25519`
- `id_ed25519.pub` - public key

These files are the global ssh key your git installation will use. You can rename the files and generate a new ssh key for another account. I tack the username for the account onto the filenames:

- `id_ed25519-crybx`
- `id_ed25519-crybx.pub`

Whichever account you want to use to auth through ssh with needs to be the files named `id_ed25519` and `id_ed25519.pub`. Any with username appended are not currently being used.

You can rename the files every time you want to switch, or...

## use multiple ssh keys without file renaming

You can configure individual repositories to use a specific ssh key (e.g. one with a username appended).

This approach ensures that the designated key is used whenever you interact with that repo, without affecting other repos.

- Locate the repo's config file: Navigate to the root directory of your local git repo in the terminal. The config file is located in the .git subdirectory and is named config.
- Edit the config file: Use any text editor to open it.
- Add or modify the core.sshCommand setting: Under the [core] section, add or modify the sshCommand setting to specify the ssh key to use for the repository. The format for this setting is:

```
[core]
    sshCommand = ssh -i /path/to/your/private_key -F /dev/null`
```

for my user

```
[core]
    sshCommand = ssh -i ~/.ssh/id_ed25519-crybx -F /dev/null
```


Replace /path/to/your/private_key with the actual path to your private key file. The -F /dev/null option prevents SSH from using the global ssh configuration file, ensuring that only the specified key is used.
For example, if your private key is located at ~/.ssh/my_repo_key, the setting would look like this:
[core]
sshCommand = ssh -i ~/.ssh/my_repo_key -F /dev/null

- Save the changes: Save the modified config file.
- Verify the configuration: To confirm that the config is set correctly, you can use:

```
git config core.sshCommand
```
This will output the configured sshCommand value, allowing you to verify that it is pointing to the correct ssh key.

compare to global:

```
git config --global core.sshCommand
```

With this config in place, git will automatically use the specified ssh key when cloning, fetching, and pushing with the repo.

### remember to update user and email for commits

You went to all that trouble to use a separate ssh key, don't forget your username and email. Inside the repo that should use the different username and email address:

```
git config user.name "2ndusername"     
git config user.email "2nduseremailaddress"
```

Compare global vs local credentials:

```
git config user.name     
git config user.email
git config --global user.name     
git config --global user.email
```
