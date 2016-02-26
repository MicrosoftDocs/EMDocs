<properties pageTitle="Steps to follow when you retire or change the name of an EMS technical article" description="Steps to follow when you retire or change the name of an EMS technical article." metaKeywords="" services="" solutions="" documentationCenter="" authors="v-jocgar" videoId="" scriptId="" manager="robmazz" />

<tags ms.service="contributor-guide" ms.devlang="" ms.topic="article" ms.tgt_pltfrm="" ms.workload="" ms.date="02/24/2016" ms.author="v-jocgar" />

# Steps to follow when you rename or retire an EMS technical article
To do:
- [ ] Confirm this is how retiring content will work for EMS
- [ ] How closely do these procedures model the internal process? Is this guide for external writers only? 
- [ ] Get the link for the EMS docs landing page
- [ ] Do we use FWLink tool? If not, remove Step 3
- [ ] Confirm the URLs marked in red

This guidance is for SMEs who are listed as the author of an article that needs to be retired from the technical documentation section of docs.microsoft.com/ems. The steps also apply if a file is renamed.

If you're a member of our EMS community and you think an article should be retired for any reason, please leave a comment <!-- in the Disqus comment stream --> for the article to let the author know something is wrong with the article.

Subject Matter Expert (SME) authors need to follow several steps to gracefully retire content so users of the website don't have a bad experience when we retire content from the site. Deleting the article or changing its name should be the last thing that happens!

## Step 1: Manage inbound links

Determine if there are any non-Microsoft inbound links to your content. Quite often blogs, forums, and other content on the web points to articles. Frequently, you can work with blog owners to change these links, and you can remove or update links from forum posts. Web analytics tools can tell you if there are any high-traffic, inbound links you might need to manage in this way.

## Step 2: Remove all cross-links to the article from the technical content repository

1. Ensure you are working in an up-to-date local branch – run `git pull origin master` (or the appropriate variation on this command).

2.	Scan the emdocs-pr/articles folder and the emdocs-pr/includes folder for any articles and includes that link to the article you want to retire, and either remove the cross-links or replace them with an appropriate new cross-links. You can use a search and replace utility to find the cross-links if you have one installed. If you don't, you can use Windows PowerShell for free! Here's how to use PowerShell to find the cross-links:

 a. Start Windows PowerShell.

 b. At the PowerShell prompt, change into the emdocs-pr\articles folder:

 `cd emdocs-pr\articles`

 c. Type this command, which will list all files that contain a reference to the article you are deleting:

 `Get-ChildItem -Recurse -Include *.md* | Select-String "<the name of the topic you are deleting>" | group path | select name`

  If you prefer to send the list of file names to a text file (in this case, named psoutput.txt), you can:

  `Get-ChildItem -Recurse -Include *.md* | Select-String "<the name of the topic you are deleting>" | group path | select name | Out-File C:\Users\<your account>\psoutput.txt`

3. Add and commit all your changes, push them to your origin, and create a pull request to move your changes from your origin to the master branch of the main repository.

## Step 3: Update the FWLink tool
<span style="color:red;">Confirm that this step is necessary or required.</span>

Check the FWLink tool for any FWLinks that might point to the article. Point any FWLinks at replacement content; if you are not on the alias that owns the link, join it. If the owners won't update the link, file a ticket with MSCOM to have the link changed. 

## Step 4: Remove all cross-links 

If there are to the article from other pages on <span style="color:red;">Confirm this URL</span> http://docs.microsoft.com/ems, you need to remove them and create a redirect for the retired page, if appropriate. You'll have to work with the person who maintains and updates the documentation landing page for your service for this part. Contact your content team partner if you don't know who that person is. The person who maintains and updates the doc landing page will need to do two things:

1. In Visual Studio, scan the **entire** EMS web solution for cross references to the file to retire. Remove the cross references, or replace them with an updated cross reference. You'll need to remove the HTML links as well as the related resource strings for the HTML links. More info - see the <span style="color:red;">Get a replacement link</span> [Replacement link for service landing page](need service landing page for left nav)

2. If a replacement article exists, create a redirect. More info - see the <span style="color:red;">Confirm the URL</span> [Replacement Link for Removing Published Pages](location of replacement topic on retiring pages).

3. Check the changes into the repository.

## Step 5: Retire the article

After you've completed the three prior steps and those changes are live, then you can delete the article from the repository.

## Step 6: Remove links from MSDN

Review the content QA tool for broken links to the retired or renamed topic and remove or fix the links in all affected MSDN topics.

## Step 7: Remove cached pages from search engines

Do this ONLY if the content needs to be removed quickly due to legal or severe customer issues. Normal priority page deletions should just be handled by natural search engine processes. Go to these web pages to remove cached web pages from search engines:

[Bing](https://www.bing.com/webmaster/tools/content-removal?rflid=1)
[Google](https://www.google.com/webmasters/tools/removals?pli=1)


### Back to Home

- [Overview article](./../README.md)
- [Index of guidance articles](./contributor-guide-index.md)
