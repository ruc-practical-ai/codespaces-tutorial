# Codespaces Tutorial

## Introduction

GitHub Codespaces provide an easy way to get started developing. It is important to know how to set up a development environment manually so we can understand how development environments work and what tools comprise suitable environments for our purposes, but Codespaces can help expedite the time it takes to start a new project by automating this.

For those familiar with Docker, codespaces are similar, but abstract away many of the details of working with containers to enable a seamless remote development experience with little preparation work on the user's side. The codespace, all its dependencies, how it is built and installed, are all defined in a `.devcontainer/devcontainer.json` file. This file is used to build the container from an image. Codespaces integrate seamlessly with VS Code, and even allow specification of VS Code configuration settings which will be active in the codespace. This allows us to have consistent VS Code configurations across collaborators, and to use different configurations across projects, all while leaving our local settings unchanged.

You can learn about Codespaces through GitHub's [documentation](https://docs.github.com/en/codespaces/overview) and watch a short video [here](https://docs.github.com/en/codespaces). This tutorial provides some basic resources to help you get started working with Codespaces in your browser and through VS Code.

## Usage

You can use codespaces in a browser or in local VS Code. Both are covered here.

### Using Codespaces in a Browser

The easiest way to use Codespaces is in a web browser. Navigate to the repository you are interested in working on and click on the `code` &rarr; `codespaces` &rarr; `create codespace on main` buttons. A VS Code window will open in your browser so you can work on the files in the repository as you normally would.

The upside of using codespaces in a web browser is that absolutely zero setup is required. This method of using codespaces is excellent for demonstrating intermediate work-products to collaborators, and especially to non-technical stakeholders who might not want to set up development environments and might not even have VS Code installed. The downside is that some features, especially `matplotlib` widgets, might not work well.

### Using Codespaces in Local VS Code - Connect from VS Code

To get more flexibility, you can use your local VS Code installation to connect to a Codespace. This allows you to use your local VS Code as a one stop resource for developing in local and remote repositories, using your own development environment or a remote environment as desired. To do this, you will need to first take care of some [prerequisites](https://docs.github.com/en/codespaces/developing-in-a-codespace/using-github-codespaces-in-visual-studio-code#prerequisites).

Follow the instructions there to first install the Github Codespaces extension for VS Code. With the extension installed, click the Remote Explorer icon, then click GitHub Codespaces, and then sign in with your Git credentials.

Once signed in, you can create a new codespace by clicking `+` on the Remote Explorer sidebar. Type the name of the repository you want to develop in there (e.g., the name of one of your assignments). Click the branch you want to develop on and the machine you want to use.

If you want to use an existing codespace, click the plug icon to connect to it.

### Using Codespaces in Local VS Code - Connect from Browser

One of the easiest ways to use local VS Code to connect to a remote codespace is to open the codespace in the browser and then click on the `code` &rarr; `codespaces` &rarr; `create codespace on main` buttons.

Once the codespace is open in the browser, click the three bars in the top left corner and select `Open in VS Code Desktop`.

### Advanced: Using Codespaces in Local VS Code with Locally Hosted Containers

GitHub provides 120 CPU-hours / month free of charge when using codespaces with a container hosted by GitHub.  This is convenient since GitHub handles everything involved with setting up the container in which the codespace environment runs. However, if we spend a lot of time in codespaces or use CPU-intensive processes we may wish to host containers locally ourselves. This is more difficult to setup, and the exact setup steps will be highly system dependent, but it is worth it for those who wish to write a lot of code and have complete control of every layer of their development environment.

Follow the setup tutorial [here](https://code.visualstudio.com/docs/devcontainers/containers) for full instructions. A summary of these instructions is included below.

#### Prerequisites

To use codespaces on a locally hosted container, you first need a means of hosting a container on your local machine.

Follow the instructions [here](https://www.docker.com/products/docker-desktop/) to install Docker Desktop.

If Docker Desktop is already installed on your machine, be sure to update it by starting Docker Desktop and clicking `Update to Latest` (in the top-left corner) &rarr; `Download Updates` &rarr; `Update and Restart`. If asked to kill applications, ensure you are not currently using anything relying on Docker Desktop and when ready click `Kill Applications`. Wait for the installer to run and finish before proceeding.

#### Prerequisites (Windows-Specific)

For Windows users it is recommended to install Docker Desktop on top of Windows Subsystem Linux (WSL) 2. If WSL 2 is not already installed and set up, follow the instructions [here](https://docs.docker.com/desktop/wsl/).

Once WSL 2 is installed and configured, if you have not already done so, ensure that Docker Desktop is configured to use it.

Right click on the Docker Desktop taskbar icon and select `Settings`. Check `Use the WSL 2 based engine`. In the settings menu, also select `Enable Docker Terminal`. Click `Apply` and `Restart`.

**Tip for Windows**: If you click Docker Desktop and it does not open, try looking in the task bar to see if it is already open. Stop and restart Docker Desktop from the taskbar if necessary.

It may be necessary to reboot after installing Docker Desktop or WSL 2.


#### Open a Repository in a Local Container

When you clone a repository with a `.devcontainer` in it and open it in local VS Code, you may be prompted to open the repository in a container. If you are, you can click the button shown to open the repository.

If you are not prompted, use `Ctrl/Cmd` + `Shift` + `P` &rarr; Type `Dev Containers: Reopen in Container` to open the repository in a local container.

If you do not see this command, install (or uninstall and reinstall) the Dev Containers extension by Microsoft. Restart VS Code if necessary.

#### Configure Git for Local Container

When you open a repository in a local container and run a git command (e.g., `git status`) you may get a security warning. Follow the recommendations and add an exception.

```bash
git config --global --add safe.directory RECOMMENDED_DIRECTORY
```

#### Remove Unused Containers

Be sure to remove containers when you are done using them. You can do this from VS Code by clicking on the Remote Explorer extension. Click the `x` next to the container you want to stop.

You can also remove containers directly from Docker Desktop by clicking the `Delete` button corresponding to the container you want to delete.

**Warning**: be sure you do not have any uncommitted changes in the container you are deleting, or any unsaved files that have not been committed to git or saved on your local drive. Once you delete the container, any unsaved files or files only saved on the container itself and not saved on your local machine or push to git will be gone forever!

### Tips

#### Checking Codespace Creation Status

Some codespaces in this class might take a long time to build, especially codespaces that have dependencies on latex or tex-live.  Use `Cmd` / `Ctrl` + `Shift` + `P` &rarr; `Codespaces: View Creation Logs` to check status.

#### Rebuilding the Container

The codespace and all its dependencies are are defined in the devcontainer. If we make changes to the devcontainer, we need to reload it for those changes to take effect. Use `Cmd` / `Ctrl` + `Shift` + `P` &rarr; `Codespaces: Rebuild Container` to rebuild the container.

Do not use `gh codespace rebuild` unless you really want to rebuild the entire image (including the base container environment that the codespace is built from, which in most cases in this class we leave unchanged). This takes a long time since it re-downloads the entire image.

#### VS Code Tips and Tricks

VS Code has some [tips and tricks](https://code.visualstudio.com/docs/devcontainers/tips-and-tricks) for working with devcontainers and codespaces that are helpful to read.

### Limitations

Note that codespaces have some limitations, especially when using VS Code in the web. See VS Code's [page](https://code.visualstudio.com/docs/remote/codespaces) for more details.

One limitation is that using codespaces in a browser might make viewing plots difficult. If using codespaces in a browser, you will need to view plots in Jupyter or save them as files rather than view them by spawning new windows in Python. These issues can be mitigated by opening the codespace in local VS Code.

## Codespaces in this Class

In this class (and professionally), you are expected to know how to set up a local development environment yourself and to work in codespaces. You are expected to know when it is appropriate to use either mode of working, and be able to switch between local and remote development to best serve your project and goals for that particular programming session.

The expectation that you know how to maintain a local development environment (in addition to knowing how to use codespaces) is held so that you can (1) understand all the required tools that help your programs run under the hood and (2) be ready to build your own development environments using more advanced tools like Docker, or even your own codespaces later on. When you build these environments, you provide tools like Docker and Codespaces all the commands needed to automate all the set up that goes into standing up a development environment. Having done this manually while maintaining your own environment in the safety of an academic setting ensures that you are qualified to do it automatically via those tools later!

All assignments in this course will come with the proper *dotfiles* (i.e., hidden files that begin with a `.`) to define that assignment's codespace if you need it.

As is the theme with this course, if the tests pass and the work was your own, you will get full credit for any assignment regardless of the tools you prefer to use to complete it.

## Codespaces for Machine Learning

GitHub has a great tutorial on [setting up codespaces for machine learning](https://docs.github.com/en/codespaces/developing-in-a-codespace/getting-started-with-github-codespaces-for-machine-learning).

You can optionally go through this tutorial on your own, or wait until we go through it together in class.

## Advanced and Optional: Configuring Your Own Codespace

If you want to try [creating or configuring your own codespace](https://docs.github.com/en/codespaces/developing-in-a-codespace/creating-a-codespace-for-a-repository), you are encouraged to do so. This is not required in this course, but you may find it helpful in other work you do, academically and professionally. You will also see why it helps to understand how and where these tools are installed inside a container, codespace (built on containers), or your local machine, when building more complex systems.

You can learn how to do this by defining the right dotfiles in your repository [here](https://docs.github.com/en/codespaces/setting-up-your-project-for-codespaces/adding-a-dev-container-configuration/introduction-to-dev-containers).

You can deep dive into codespaces if interested [here](https://docs.github.com/en/codespaces/getting-started/deep-dive).