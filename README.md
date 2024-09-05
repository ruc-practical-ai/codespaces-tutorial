# Codespaces Tutorial

## Introduction

GitHub Codespaces provide an easy way to get started developing. It is important to know how to set up a development environment manually, but Codespaces can help expedite the time it takes to start a new project by automating this.

You can learn about Codespaces through GitHub's [documentation](https://docs.github.com/en/codespaces/overview) and watch a short video [here](https://docs.github.com/en/codespaces). This tutorial provides some basic resources and gets you started working with Codespaces in your browser and through VSCode.

## Usage

You can use codespaces in a browser or in local VSCode. Both are covered here.

### Using Codespaces in a Browser

The easiest way to use Codespaces is in a web browser. Navigate to the repository you are interested in working on, click the `Code` button, click `Codespaces`, and click `Create codespace on main`. A VSCode window will open in your browser so you can work on the files in the repository as you normally would.

### Using Codespaces in Local VSCode

It is convenient to use your local VSCode installation to connect to a Codespace. To do this, you will need to first take care of some [prerequisites](https://docs.github.com/en/codespaces/developing-in-a-codespace/using-github-codespaces-in-visual-studio-code#prerequisites).

Follow the instructions there to first install the Github Codespaces extension for VSCode. With the extension installed, click the Remote Explorer icon, then click GitHub Codespaces, and then sign in with your Git credentials.

Once signed in, you can create a new codespace by clicking `+` on the Remote Explorer sidebar. Type the name of the repository you want to develop in there (e.g., the name of one of your assignments). Click the branch you want to develop on and the machine you want to use.

If you want to use an existing codespace, click the plug icon to connect to it.

### Limitations

Note that codespaces have some limitations, especially when using VSCode in the web. See VSCode's [page](https://code.visualstudio.com/docs/remote/codespaces) for more details.

One limitation is that using codespaces in a browser might make viewing plots difficult. If using codespaces in a browser, you will need to view plots in Jupyter or save them as files rather than view them by spawning new windows in Python.

## Codespaces in this Class

In this class, you are expected to know how to set up a local development environment yourself. This is so that you can (1) understand all the required tools that help your programs run under the hood and (2) be ready to build your own development environments using more advanced tools like Docker, or even Codespaces later on. When you build these environments, you provide tools like Docker and Codespaces all the commands needed to automate all the set up that goes into standing up a development environment. Having done this manually ensures that you are qualified to do it automatically via those tools!

Professionally, you are expected to know how to set up both local and remote development environments for different projects using a variety of tools. Knowing how to set up a local development environment manually will prepare you to set one up using any other tools.

Using your own development environment is the preferred method for completing assignments in this class for those reasons. However, to ensure that the class is accessible to all, on any computer, using Git Hub codespaces is always allowed as a backup plan.

All assignments in this course will come with the proper *dotfiles* (i.e., hidden files that begin with a `.`) to define that assignment's codespace if you need it.

As is the theme with this course, if the tests pass and the work was your own, you will get full credit for any assignment regardless of the tools you prefer to use to complete it.

## Codespaces for Machine Learning

GitHub has a great tutorial on [setting up codespaces for machine learning](https://docs.github.com/en/codespaces/developing-in-a-codespace/getting-started-with-github-codespaces-for-machine-learning).

You can optionally go through this tutorial on your own, or wait until we go through it together in class.

## Advanced and Optional: Configuring Your Own Codespace

If you want to try [creating or configuring your own codespace](https://docs.github.com/en/codespaces/developing-in-a-codespace/creating-a-codespace-for-a-repository), you are encouraged to do so. This is not required in this course, but you may find it helpful in other work you do, academically and professionally. You will also see why it helps to understand how and where these tools are installed inside a container, codespace (built on containers), or your local machine, when building more complex systems.

You can learn how to do this by defining the right dotfiles in your repository [here](https://docs.github.com/en/codespaces/setting-up-your-project-for-codespaces/adding-a-dev-container-configuration/introduction-to-dev-containers).

You can deep dive into codespaces if interested [here](https://docs.github.com/en/codespaces/getting-started/deep-dive).