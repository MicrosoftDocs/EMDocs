<properties 
	pageTitle="Install and set up tools for authoring in GitHub" 
	description="Tools and steps to get set up for authoring EMS content in GitHub." 
	services="contributor-guide" 
	documentationCenter="" 
	authors="v-jocgar"  
	manager="robmazz" />

<tags 
	ms.service="contributor-guide"
	ms.devlang="" 
	ms.topic="article"
	ms.tgt_pltfrm="" 
	ms.workload="" 
	ms.date="02/19/2016" 
	ms.author="tysonn" />

# Install and set up tools for authoring in GitHub
To Do:
- [ ] Are we using Disqus? ** <-- Robert **
- [ ] Update instructions for Microsoft employees contributing to EMS vs Azure
- [ ] Robert to ask Liza if she will respond to testing this procedure
- [ ] Use Git for Git Bash only?

Follow the steps in this article to set up tools for contributing to the EMS technical documentation. Casual and occasional contributors probably can use the GitHub UI described in step 2.

If you're unfamiliar with Git, you might want to review some Git terminology: [https://help.github.com/articles/github-glossary](https://help.github.com/articles/github-glossary). In addition, this StackOverflow thread contains a glossary of Git terms you'll encounter in this set of steps: [http://stackoverflow.com/questions/7076164/terminology-used-by-git](http://stackoverflow.com/questions/7076164/terminology-used-by-git)

## Contents

- [Create a GitHub account and set up your profile](#create-a-github-account-and-set-up-your-profile)
<!-- - [Sign up for Disqus](#sign-up-for-disqus) -->
- [Determine whether you really need to follow the rest of these steps](#determine-whether-you-really-need-to-follow-the-rest-of-these-steps)
- [Permissions in GitHub](#permissions-in-github)
- [Install Git for Windows](#install-git-for-windows)
- [Enable two-factor authentication](#enable-two-factor-authentication)
- [Install a markdown editor](#install-a-markdown-editor)
- [Configure Atom](#configure-atom)
- [Create a branch from the repository and copy it to your computer](#create-a-branch-from-the-repository-and-copy-it-to-your-computer)
- [Configure your user name and email locally](#configure-your-user-name-and-email-locally)
- [Next steps](#next-steps)

## Create a GitHub account and set up your profile

To contribute to the EMS technical content, you'll need a [GitHub](http://www.github.com) account.

If you are a Microsoft contributor, you need to set up your GitHub account so you're clearly identified as a Microsoft employee. Set up your profile as follows:

- **Profile picture**: a picture of you (required)
- **Name**: your first and last name (required)
- **Email**: your Microsoft email address (required)
- **Company**: Microsoft Corporation (required)
- **Location**: list your location (required)

Your profile should resemble this profile:

 ![GitHub profile example](./media/githubprofile.png)

<!-- Are we even using Disqus? 
## Sign up for Disqus

Every published EMS technical article has a comment stream provided by the Disqus service.

 ![Discus logo](./media/discus.png)

If you are a Microsoft employee, and if you are the author of or a contributor to an article, you need to sign up for Disqus so you can participate in the comment stream for the article.

1. Sign up for an account at [http://www.disqus.com/](http://www.disqus.com/)
2. Fill out your profile as follows:

 - **Full Name**: your full name as displayed in your Microsoft address book listing, plus the bracketed info, which is your alias plus @MSFT. Format: *First Last [alias@MSFT]*
 - **Location**: Your location
 - **Short Bio**: Your title
-->
## Determine whether you really need to follow the rest of these steps

You might not need to follow all the steps in this article. It depends on the sort of content contribution you want or need to make.

### Submit a text-only change to an existing article

If you only need or want to make textual updates to an existing article, you probably don't need to follow the rest of the steps. You can use GitHub's web-based markdown editor to submit your changes. Just click the GitHub link in the article you want to modify:

 ![GitHub profile example](./media/contributetogit.png)

 Then, click the edit icon in the GitHub version of the article

 ![GitHub profile example](./media/editicon.png)

 That opens the easy-to-use web editor that makes it easy to submit changes. You don't need to follow the other steps in this article.

### All other changes
You need to install the tools if you want to make any of the following sorts of changes:

 - Major changes to an article
 - Create and publish a new article
 - Add new images or update images
 - Update an article over a period of days without publishing changes each of those days

 Go to the next section!

## Permissions in GitHub

Anybody with a GitHub account can contribute to EMS technical content through our public repository at [http://www.github.com/microsoft/emdocs](http://www.github.com/microsoft/emdocs). No special permissions are required.

<!-- Need updated instructions here -->
If you are a Microsoft employee working on EMS content, you should work in our private content repository, ems-content-pr. Visit [*Need replacement link*](http://aka.ms/somelink) to obtain the read permissions that will let you make contributions through the private repo - sign in to GitHub using the button > click EMS > click **Join a team** or **Join another team**, and then search for and join the **ems-content-read** group.

## Install Git for Windows

Install Git for Windows from [http://git-scm.com/download/win](http://git-scm.com/download/win). This download installs the Git version control system, and it installs Git Bash, the command-line app that you will use to interact with your local Git repository.

 ![GitHub profile example](./media/gitbashinstall.png)

(Note: This program is not the same as "Github for Windows". "Github for Windows" is a different GUI-based tool that will also work if you want to read up on yourself. [https://windows.github.com/](https://windows.github.com/)) 

## Enable two-factor authentication

You have to enable two factor authentication (2FA) on your GitHub account if you are working in the private content repository: it's required.

To enable this, follow the instructions in both the following GitHub help topics:

- [About Two-Factor Authentication](https://help.github.com/articles/about-two-factor-authentication/)

## Create a personal access token
The personal access token authenticates you and the computer you're working on to GitHub.
1. In GitHub, click yourself, then click Settings.
2. On the Personal Access Token tab, click Generate new token.
3. Give the token a description. 
4. Set the scope. You’ll want to have full access to the repo and user.
5. Click Generate token.
6. Copy the displayed token and paste it into a safe place, like an email or Word doc. You need this token to pull and push to GitHub.

## Install a markdown editor

We author content using simple "markdown" notation in the files, rather than complex "markup" (HTML, XML, etc.). So, you'll need to install a Markdown editor.

- **Atom**: Most of us use GitHub's Atom Markdown editor: [http://atom.io](http://atom.io). It does not require a license for business use. It has spell check. 

- **Notepad**: You can use Notepad for a very lightweight option.

- **Prose**: This is a lightweight, elegant, on-line, and open source markdown editor that offers a preview. Visit [http://prose.io](http://prose.io) and authorize Prose in your repository.

- **[Visual Studio Code](https://www.visualstudio.com/products/code-vs.aspx)** - Microsoft's entry in this space.

## Configure the Atom Markdown editor

If you use Atom, you'll need to set a few things up.

- Atom defaults to using 2 spaces for tabs, but Markdown expects 4 spaces. If you leave it at the default of two, your article will look great in local preview, but not when it’s imported into docs.microsoft.com. So, configure Atom to use 4 spaces - you can find this setting under File->Settings->Editor Settings->Tab Length. 
- You will probably also want to turn on Soft Wrap in this section too, which does the same as "word wrap" in Notepad. 
- To turn on the markdown preview, click Packages->Markdown Preview->Toggle Preview. You can use Ctrl-Shift-M to toggle the preview HTML view. 

## Create a branch from the repository and copy it to your computer

1. Create a branch from the repository in GitHub. At the command line....

2. Open Git Bash and run it as an administrator. At the command prompt, enter the following command. This command creates a emdocs(-pr) drectory on your computer.  If you're using the default location, it will be at c:\users<your Windows user name>\emdocs(-pr).

Public repo:

        git clone https://[your GitHub user name]:[token]@github.com/microsoft/emdocs.git

Private repo:

        git clone https://[your GitHub user name]:[token]@github.com/microsoft/emdocs-pr.git

For example, this clone command could look something like this:

        git clone https://smithj:b428654321d613773d423ef2f173ddf4a312345@github.com/microsoft/emdocs-pr.git  

## Set remote repository connection and configure credentials

Configure git to use your GitHub ID and personal access token by default so you don't have to manually type or paste that access token for each `push` or `pull` action. Run the following command in git bash:

Public repo:

		cd emdocs
		git remote –v 
		git remote remove origin
		git remote add origin http://<githubID>:<token>@github.com/microsoft/emdocs
		git remote -v

Private repo:

		cd emdocs-pr
		git remote –v 
		git remote remove origin
		git remote add origin http://<githubID>:<token>@github.com/microsoft/emdocs-pr
		git remote -v

This usually takes a while. After you do this, you won't have to enter your credentials again. You would only have to repeat the process again if you set the tools up on another computer.

## Configure your user name and email locally

To ensure you are listed correctly as a contributor, you need to configure your user name and email locally in Git.

1. Start Git Bash, and switch into emdocs or emdocs-pr:

   ````
   cd emdocs
   ````

 or

   ````
   cd emdocs-pr
   ````

2. Configure your user name so it matches your name as you set it up in your GitHub profile:

    ````
    git config --global user.name "John Doe"
    ````
3. Configure your email so it matches the primary email designated in your GitHub profile; if you're a Microsoft employee, it should be your Microsoft email address:

    ````
    git config --global user.email "alias@example.com"
    ````
4. Type `git config -l` and review your local settings to ensure the user name and email in the configuration are correct.

## Next steps

- [Create a local working branch](./git-commands-for-master.md) on your computer so you can start work.


## Back to Home

- [Overview article](./../README.md)
- [Index of guidance articles](./contributor-guide-index.md)


<!--Anchors-->
[Use a customer-friendly voice]: #use-a-customer-friendly-voice
[Consider localization and machine translation]: #consider-localization-and-machine-translation
[other style and voice issues to watch for]: #other-style-and-voice-issues-to-watch-for


[Create a GitHub account and set up your profile]: #create-a-github-account-and-set-up-your-profile
[Determine whether you really need to follow the rest of these steps]: #determine-whether-you-really-need-to-follow-the-rest-of-these-steps
[Permissions in GitHub]: #permissions-in-github
[Install Git for Windows]: #install-git-for-windows
[Enable two-factor authentication]: #enable-two-factor-authentication
[Install a markdown editor]: #install-a-markdown-editor
[Fork the repository and copy it to your computer]: #fork-the-repository-and-copy-it-to-your-computer
[Install git-credential-winstore]: #install-git-credential-winstore
[Configure your user name and email locally]: #configure-your-user-name-and-email-locally
[Next steps]: #next-steps
