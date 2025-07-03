# Creating `.devcontainer` Templates

> *The goal of this guide will be to create several templates as well as templates of templates to quickly create devcontainers for rapid development on GitHub codespaces*

---

## Documents in this repo

- [Project configuration folders](docs/project-configuration-folders.md)
- [Naming Conventions](docs/naming-conventions.md)

---

## What are Development Containers?

A development container (or dev container for short) allows you to use a container as a full-featured development environment. It can be used to run an application, to separate tools, libraries, or runtimes needed for working with a codebase, and to aid in continuous integration and testing. Dev containers can be run locally or remotely, in a private or public cloud, in a variety of [supporting tools and editors](https://containers.dev/supporting). [[Source]](https://containers.dev/)

## [containers.dev](https://containers.dev)

[containers.dev](https://containers.dev) is a Microsoft run repository hosting development containers. The GitHub repo for the website is [@devcontainers/devcontainers.github.io](https://github.com/devcontainers/devcontainers.github.io)

## Template development container repositories 

These existing template repositories will be handy to build development containers from:

- [**Jekyll**](https://github.com/devcontainers/templates/tree/main/src/jekyll) - Ruby based static site generator used by GitHub for GitHub Pages. 
- **[Nodejs](https://github.com/devcontainers/templates/tree/main/src/javascript-node)** - Server side JavaScript development environment. Uses NPM (Node package manager).

## Vanilla Node.js `.devcontainer` file

[`devcontainer/.devcontainer.json`](https://github.com/devcontainers/templates/blob/main/src/javascript-node/.devcontainer/devcontainer.json) file
*(from the [javascript-node devcontainer template repo](https://github.com/devcontainers/templates/blob/main/src/javascript-node/.devcontainer/devcontainer.json))*

```json
// For format details, see https://aka.ms/devcontainer.json. For config options, see the
// README at: https://github.com/devcontainers/templates/tree/main/src/javascript-node
{
	"name": "Node.js",
	// Or use a Dockerfile or Docker Compose file. More info: https://containers.dev/guide/dockerfile
	"image": "mcr.microsoft.com/devcontainers/javascript-node:1-${templateOption:imageVariant}"

	// Features to add to the dev container. More info: https://containers.dev/features.
	// "features": {},

	// Use 'forwardPorts' to make a list of ports inside the container available locally.
	// "forwardPorts": [],

	// Use 'postCreateCommand' to run commands after the container is created.
	// "postCreateCommand": "yarn install",

	// Configure tool-specific properties.
	// "customizations": {},

	// Uncomment to connect as root instead. More info: https://aka.ms/dev-containers-non-root.
	// "remoteUser": "root"
}
```

The most important string for our purposes is the node docker image URL [`mcr.microsoft.com/devcontainers/javascript-node`](https://mcr.microsoft.com/devcontainers/javascript-node).

Do note the [`:1-${templateOption:imageVariant}`](https://github.com/devcontainers/templates/blob/main/src/javascript-node/devcontainer-template.json) added onto the above string. This is to allow different image variants that can be referenced from the [`devcontainer-template.json`](https://github.com/devcontainers/templates/blob/main/src/javascript-node/devcontainer-template.json) file in the root of the repo.

## Creating a Simple Dev Container

First I will create our first development container simply by copying it from an existing source.

I’ll aim to make a vanilla nodejs (@ the latest version) devcontainer file with no other addons or plugins.

- 

## Work Process

1. Create a simple nodejs `.devcontainer.json` file and environment and test it.
2. Create a `devcontainer-template.json` that will outline all keys and common or potential values. 
3. Create templates for dotfiles
4. Templates for GitHub Actions for different environments (dev, testing, deployment)
   1. Linting
   2. Beautification
   3. Live Reload
   4. Git Repo creation depending on deployment strategy.
5. Templates for IDE (editor) customizations (like for vscode and vscode.dev)

### Directories to look at

*From the root of a repository:*

- `.github/` - place to hold `CODE_OF_CONDUCT.md` and `CONTRIBUTING.md` files.
- `.github/workflows/` - [How to write github workflows](https://docs.github.com/en/actions/writing-workflows)
- `.dotfiles` or `.config` - A place to store CLI configurations per project.

#### Or stash all the above in a single project config folder

- `.project` or `.env` - A more sane place to store all of these per project configs. *Maybe something like:* 
  - `.project/github`
  - `.project/vscode`
  - `.project/cli/bin`
  - `.project/cli/dotfiles`

## Nice to haves

- Typescript support
- Express
- ZSH
- Oh My ZSH
- My Dotfiles for ZSH and OMZ
- Liver reloading
- Yarn or PNPM instead of NPM
