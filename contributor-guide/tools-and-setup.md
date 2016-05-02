<properties pageTitle="Install and set up tools for authoring in GitHub" description="Tools and steps to get set up for authoring EMS content in GitHub." services="contributor-guide" documentationCenter="" authors="v-jocgar" manager="robmazz" />

<tags ms.service="contributor-guide" ms.devlang="" ms.topic="article" ms.tgt_pltfrm="" ms.workload="" ms.date="02/25/2016" ms.author="v-jocgar" />

# Install and set up tools for authoring in GitHub
To Do:
- [ ] #21 Entire procedure needs to be tested with a non-Microsoft account and computer. 

Follow the steps in this article to set up tools for contributing to the EMS technical documentation. 

- If you're unfamiliar with Git, you might want to review some Git terminology: [https://help.github.com/articles/github-glossary](https://help.github.com/articles/github-glossary).
- We also highly recommend this set of videos about [Git and Github Foundations](https://www.youtube.com/playlist?list=PLg7s6cbtAD15G8lNyoaYDuKZSKyJrgwB-). They're quick and easy to follow along.  

## Step-by-step instructions

- [Create a GitHub account and set up your profile](#create-a-github-account-and-set-up-your-profile)
- [Permissions in GitHub](#permissions-in-github)
- [Install Git for Windows](#install-git-for-windows)
- [Enable two-factor authentication](#enable-two-factor-authentication)
- [Create a personal access token](#create-a-personal-access-token)
- [Install a Markdown editor](#install-a-markdown-editor)
- [Configure Atom](#configure-atom)
- [Create a branch from the repository](#create-a-branch-from-the-repository)
- [Set remote repository connection and configure credentials](#set-remote-repository-connection-and-configure-credentials)
- [Configure your user name and email locally](#configure-your-user-name-and-email-locally)
- [Next steps](#next-steps)

## Create a GitHub account and set up your profile

To contribute to EMS technical content, you'll need a [GitHub](http://www.github.com) account.

- **Profile picture**: a picture of you (required)
- **Name**: your first and last name (required)
- **Email**: your email address (required)
- **Company**: your company (required)
- **Location**: list your location (required)

Your profile should resemble this profile:

 ![GitHub profile example](./media/githubprofile.png)

## Permissions in GitHub

Anybody with a GitHub account can contribute to EMS technical content through our public repository at [http://www.github.com/microsoft/emdocs](http://www.github.com/microsoft/emdocs). No special permissions are required.

## Install Git for Windows

Install **Git for Windows** from [http://git-scm.com/download/win](http://git-scm.com/download/win). This download installs the Git version control system, and it installs Git Bash, the command-line app that you will use to interact with your local Git repository.

**Note**
This program is not the same as "Github for Windows". "Github for Windows" is a different GUI-based tool that will also work if you want to read up on yourself. [https://windows.github.com/](https://windows.github.com/)) 

During setup you have the opportunity to select how you'll interact with the Github repository. We recommend that you use Git from Git Bash only. 
 ![GitHub profile example](./media/gitbashinstall.png)

## Enable two-factor authentication

You are required to enable two factor authentication (2FA) on your GitHub account if you are working in the private content repository. To enable this, follow the instructions in the following GitHub help topic:

- [About Two-Factor Authentication](https://help.github.com/articles/about-two-factor-authentication/)

## Create a personal access token
The personal access token authenticates you and the computer you're working on to GitHub.
1. In GitHub, click yourself, then click Settings.
2. On the Personal Access Token tab, click Generate new token.
3. Give the token a description. 
4. Set the scope. You'll want to have full access to the repository and user by checking those permission checkboxes.
5. Click Generate token.
6. Copy the displayed token and paste it into a safe place, like an email or Word doc. You need this token to pull and push to GitHub.

## Install a markdown editor

We author content using simple "Markdown" notation in the files, rather than complex "markup" (HTML, XML, etc.). So, you'll need to install a Markdown editor. We do use the Github-flavored Markdown. 

- **Atom**: Most contribtors use GitHub's Atom Markdown editor: [http://atom.io](http://atom.io). It does not require a license for business use and it has spell check. 
- **Notepad**: You can use Notepad for a very lightweight option.
- **Prose**: This is a lightweight, elegant, on-line, and open source markdown editor that offers a preview. Visit [http://prose.io](http://prose.io) and authorize Prose in your repository.
- **[Visual Studio Code](https://www.visualstudio.com/products/code-vs.aspx)** - Microsoft's entry in this space.
- **MarkdownPad 2**: You can use [MarkdownPad 2](http://markdownpad.com/) for free, but if you purchase a license, you can take advantage of the Github-flavored Markdown rendering in the Live Preview.  

## Configure the Atom Markdown editor

If you use Atom, you'll need to set a few things up.

- Atom defaults to using 2 spaces for tabs, but Markdown expects 4 spaces. If you leave it at the default of two, your article will look great in local preview, but not when it's imported into docs.microsoft.com. So, configure Atom to use 4 spaces - you can find this setting under File->Settings->Editor Settings->Tab Length. 
- You will probably also want to turn on Soft Wrap in this section too, which does the same as "word wrap" in Notepad. 
- To turn on the markdown preview, click Packages->Markdown Preview->Toggle Preview. You can use Ctrl-Shift-M to toggle the preview HTML view. 

## Create a branch from the repository

Create a branch from the repository in GitHub. 

1. Open Git Bash. 
2. At the command prompt, enter the following command. 

        git clone https://[your GitHub user name]:[token]@github.com/microsoft/emdocs.git

This command creates an `emdocs` directory on your computer.  If you're using the default location, it will be at `c:\users\<your Windows user name>\emdocs`. For example, this clone command would look something like this:

        git clone https://smithj:b428654321d613773d423ef2f173ddf4a312345@github.com/microsoft/emdocs.git  

## Set remote repository connection and configure credentials

Configure Git to use your GitHub ID and personal access token by default so you don't have to manually type or paste that access token for each `push` or `pull` action. 

Run the following command in git bash:

		cd emdocs
		git remote –v 
		git remote remove origin
		git remote add origin http://<githubID>:<token>@github.com/microsoft/emdocs
		git remote -v

This usually takes a while. After you do this, you won't have to enter your credentials again. You would only have to repeat the process again if you set the tools up on another computer.

## Configure your user name and email locally

To ensure you are listed correctly as a contributor, you need to configure your user name and email locally in Git.

1. Start Git Bash, and switch into emdocs
   ````
   cd emdocs
   ````
2. Configure your user name so it matches your name as you set it up in your GitHub profile:

    ````
    git config --global user.name "John Doe"
    ````
3. Configure your email so it matches the primary email designated in your GitHub profile:

    ````
    git config --global user.email "alias@example.com"
    ````
4. Type `git config -l` and review your local settings to ensure the user name and email in the configuration are correct.

## Next steps

- Read and follow the instructions in [Working with Git](./work-with-git.md) so you can begin writing.


## Back to Home

- [Overview article](./../README.md)
- [Index of guidance articles](./contributor-guide-index.md)


<!--Anchors-->
[Create a GitHub account and set up your profile]: #create-a-github-account-and-set-up-your-profile
[Permissions in GitHub]: #permissions-in-github
[Install Git for Windows]: #install-git-for-windows
[Enable two-factor authentication]: #enable-two-factor-authentication
[Create a personal access token]: #create-a-personal-access-token
[Install a markdown editor]: #install-a-markdown-editor
[Configure Atom]:#configure-atom
[Create a branch from the repository]: #create-a-branch-from-the-repository
[Set remote repository connection and configure credentials]: #set-remote-repository-connection-and-configure-credentials
[Configure your user name and email locally]: #configure-your-user-name-and-email-locally
[Next steps]: #next-steps