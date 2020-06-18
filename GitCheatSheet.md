# Git Cheat Sheet

Since I'm terrible at remembering these kinds of details, I created this cheat sheet to help remind me!

## Table of Contents

- [Git Cheat Sheet](#git-cheat-sheet)
  - [Table of Contents](#table-of-contents)
  - [Getting the Latest Source](#getting-the-latest-source)
  - [Saving Local Code Changes](#saving-local-code-changes)
  - [Updating the Remote Repository](#updating-the-remote-repository)
  - [Labeling a Release](#labeling-a-release)

## Getting the Latest Source

If you are starting from a new directory with no source code downloaded yet, then using the terminal, change directory to the directory that you want to contain the project directory. Then use this command:

```shell
git clone https://github.com/jdavies/TestDrive_1hr.git
```

If you just want to update your local source to get any changes from the remote repository, use the command:

```shell
git pull
```

## Saving Local Code Changes

Use the following commands to update the local repository with changes to the project

```shell
git add .
git commit -m "your comments here"
```

It's easier to do this using the Git capabilities of VSCode, but if you need to do it via command line, that's how.

## Updating the Remote Repository

Using the terminal, change into the project directory. Then:

```shell
git push origin master
```

## Labeling a Release

The following command is an example of creating a full, annotated tag for a release:

```shell
git tag -a v1.0 -m "Initial release!"
```

[Top](#table-of-contents)