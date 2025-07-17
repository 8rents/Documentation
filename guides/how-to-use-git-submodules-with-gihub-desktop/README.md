# How To Use Git Submodules with GitHub Desktop

> *A quick guide to using git submodules with GitHub Desktop*

---

In Git a submodule is a separate git repository that is added to another git repository as a dependency.

**This guide will cover:**

1. [Adding an existing repository as a submodule](#adding-an-existing-repository-as-a-submodule)
2. [Pulling and cloning submodules](#pulling-and-cloning-submodules)
3. [Updating repositories added as a submodule](#updating-repositories-added-as-a-submodule)

## Adding an Existing Repository as a Submodule

I’m going to add my GitHub profile text as a submodule called `8rents-profile` in a folder called `Profile` in this repositories root folder.

The repository URL for `8rents-profile` is `https://github.com/8rents/8rentS`.

### The `.gitmodules` file

Submodules are handled through a file in the root of the main repository called `.gitmodules`. 

Each submodule needs to include the following lines:

1. Submodule declaration
2. The path within the parent repo
3. The remote URL

The following code snippet will register a submodule called `8rents-profile` from the URL `https://github.com/8rents/8rentS` into the folder called `Profile`. 

```
[submodule "8rents-profile"]
  path = Profile
  url = https://github.com/8rents/8rentS
```

- The first line with the brackets `[submodule]` declares the submodule.
- The second line `path` says where the submodule will be cloned to in the future
- The third line `url` says where the submodule will be cloned from.

Note that you can call the submodule something different that what it is called in the remote repo. You can also place different submodules in different locations. 

To add another submodule add another declaration line:

```
[submodule "8rents-profile"]
  path = Profile
  url = https://github.com/8rents/8rentS
[submodule "submod2"]
 path = folder-for-sm2
 url = https://github.com/example-user/submodule2-example
```

You can add as many submodules as you like this way. Make sure to clone and commit them after adding these lines to the file.

## Pulling and Cloning Submodules

Fortunately GitHub Desktop makes it pretty easy to do this

## Updating repositories added as a Submodule



## Sources

- [Atlassian Guide to Git Submodules](https://www.atlassian.com/git/tutorials/git-submodule)