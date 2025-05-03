[< Git References](README.md)

# EASILY UPDATE GIT FOR WINDOWS

Since Git 2.16.1(2) you can use

`git update-git-for-windows`

In version between 2.14.2 and 2.16.1, the command was

`git update`

(It was later renamed to avoid confusion with updating the local repository, e.g. like svn update does it.)

That command does not exist in Git 2.13 and before.

If this errors with "is not a git command" then either you don't actually have Git for Windows, or your version is very old.

In which case, simply get the latest installer from https://git-scm.com/download (check whether you want 32- or 64-bit) and run it to upgrade.

If you already have the latest version it does nothing, in which case you can manually run the installer to reinstall.

```cmd
C:\> git update-git-for-windows
Git for Windows 2.17.0.windows.1 (64bit)
Up to date
```

Source: [this Stack Overflow thread](https://stackoverflow.com/questions/13790592/how-to-upgrade-git-on-windows-to-the-latest-version)
