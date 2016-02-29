<properties pageTitle="Steps to follow when you retire or change the name of an EMS technical article" description="Steps to follow when you retire or change the name of an EMS technical article." metaKeywords="" services="" solutions="" documentationCenter="" authors="v-jocgar" videoId="" scriptId="" manager="robmazz" />

<tags ms.service="contributor-guide" ms.devlang="" ms.topic="article" ms.tgt_pltfrm="" ms.workload="" ms.date="02/26/2016" ms.author="v-jocgar" />

# Steps to follow when you rename or retire an EMS technical article

To do:
- [ ] #57 Confirm this is how retiring content will work for EMS. This seems more like an internal-only set of procedures. 
- [ ] #58 Confirm that external writers would be able to run a web analytics tool against Microsoft content. 
- [ ] #59 Test the procedure for finding cross-links in the repo.
- [ ] #60 Confirm the URL for the EMS Docs.  
- [ ] #61 Confirm that removing cross-links is possible for external writers. 
- [ ] #62 Confirm that an external writer could create a redirect.
- [ ] #63 Confirm that an external writer could delete an article from the repo.
- [ ] #64 Confirm that an external writer could request removal of Microsoft content from search engines.


<span style="color:red;">Confirm this is how retiring content will work for EMS. This seems more like an internal-only set of procedures. </span>
This guidance is for Subject Matter Expert (SMEs) who are listed as the author of an article that needs to be retired from the technical documentation section of http://docs.microsoft.com/ems. The steps also apply if a file is renamed.

SME authors need to follow several steps to gracefully retire content so users of the website don't have a bad experience when we retire content from the site. Deleting the article or changing its name should be the last thing that happens!

If you're a member of our EMS community and you think an article should be retired for any reason, please leave a comment for the article to let the author know something is wrong with the article.

## Step 1: Manage inbound links

Determine if there are any non-Microsoft inbound links to your content. Quite often blogs, forums, and other content on the web points to articles. Frequently, you can work with blog owners to change these links, and you can remove or update links from forum posts. <span style="color:red;">Confirm that external writers would be able to run a web analytics against Microsoft content. </span>Web analytics tools can tell you if there are any high-traffic, inbound links you might need to manage in this way.

## Step 2: Remove all cross-links to the article from the technical content repository
<span style="color:red;">Test the procedure for finding cross-links in the repo.</span>
1. Ensure you are working in an up-to-date local branch – run `git pull origin master` (or the appropriate variation on this command).

2.	<span style="color:red;">Confirm the paths in the repo.</span> Scan the \EMDocs\Solutions folder and the \EMDocs\Token folder for any articles and tokens that link to the article you want to retire, and either remove the cross-links or replace them with an appropriate new cross-links. You can use a search and replace utility to find the cross-links if you have one installed. If you don't, you can use Windows PowerShell for free! Here's how to use PowerShell to find the cross-links:

 a. Start Windows PowerShell.

 b. At the PowerShell prompt, change into the \EMDocs\Solutions folder:

 `cd \EMDocs\Solutions`

 c. Type this command, which will list all files that contain a reference to the article you are deleting:

 `Get-ChildItem -Recurse -Include *.md* | Select-String "<the name of the topic you are deleting>" | group path | select name`

  If you prefer to send the list of file names to a text file (in this case, named psoutput.txt), you can:

  `Get-ChildItem -Recurse -Include *.md* | Select-String "<the name of the topic you are deleting>" | group path | select name | Out-File C:\Users\<your account>\psoutput.txt`

3. Add and commit all your changes, push them to your origin, and create a pull request to move your changes from your origin to the master branch of the main repository.

## Step 3: Remove all cross-links 
<span style="color:red;">Confirm that removing cross-links is possible for external writers. </span>
If there are to the article from other pages on <span style="color:red;">Confirm the URL for the EMS Docs. </span> http://docs.microsoft.com/ems, you need to remove them and create a redirect for the retired page, if appropriate. You'll have to work with the person who maintains and updates the documentation landing page for your service for this part. Contact your content team partner if you don't know who that person is. The person who maintains and updates the doc landing page will need to do two things:

1. In Visual Studio, scan the **entire** EMS web solution for cross references to the file to retire. Remove the cross references, or replace them with an updated cross reference. You'll need to remove the HTML links as well as the related resource strings for the HTML links. 

2. <span style="color:red;">Confirm that an external writer could create a redirect.</span>If a replacement article exists, create a redirect to the article. 

3. Check the changes into the repository.

## Step 4: Retire the article
<span style="color:red;">Confirm that an external writer could delete an article from the repo.</span>
After you've completed the three prior steps and those changes are live, then you can delete the article from the repository.

## Step 5: Remove cached pages from search engines
<span style="color:red;">Confirm that an external writer could request removal of Microsoft content from search engines.</span>
Do this ONLY if the content needs to be removed quickly due to legal or severe customer issues. Normal priority page deletions should just be handled by natural search engine processes. Go to these web pages to remove cached web pages from search engines:

[Bing](https://www.bing.com/webmaster/tools/content-removal?rflid=1)
[Google](https://www.google.com/webmasters/tools/removals?pli=1)


### Back to Home

- [Overview article](./../README.md)
- [Index of guidance articles](./contributor-guide-index.md)
