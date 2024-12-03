## Setup

Setting up Git to work with Github is fairly simple and just takes a little bit of setup.

##### Step 1: Directory

Creating a directory, if one isn't already created, is quite simple. You could move to the directory you'd like to have another directory within the file explorer GUI or through the command line.

If doing the command line, run:
```
mkdir [name of dir]
```
This will create a directory within the directory which you are in with the name you choose.

#### Step 2: Git Init

Next, within the directory you've made, run the command:
```
git init
```
This will initialize the directory for repository for Github.
See [official documentation](https://git-scm.com/docs/git-init) for full options.

#### Step 3: Git Status

Git status lets us see what branch we're in as well as if anything new has been created/modified/removed from the directory.
See [official documentation](https://git-scm.com/docs/git-status) for full options.

```
git status
```
This allows us to see if we need to push this dir to Github.

#### Step 4: Git add

Git add lets you add files/folders either by specificity or by all.
See [official documentation](https://git-scm.com/docs/git-add) for full options
```
git add . (add all files/folders)
```


