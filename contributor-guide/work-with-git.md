<properties pageTitle="Git commands for creating a new article or updating an existing article" description="Steps for working with the Azure technical content GitHub repositories." metaKeywords="" services="" solutions="" documentationCenter="" authors="v-jocgar" videoId="" scriptId="" manager="robmazz" />

<tags ms.service="contributor-guide" ms.devlang="" ms.topic="article" ms.tgt_pltfrm="" ms.workload="" ms.date="02/24/2016" ms.author="v-jocgar" />

# Working with Git

To do:
- [ ] Replace EMS URL for completed articles (see end of instructions)

## Standard process (working from a branch)
Follow the steps in this article to create a local working branch on your computer so that you can create a new article for the technical documentation section of Microsoft.com/ems or update an existing article.

1. Start Git Bash. 

2. Change to the repository *emdocs*:

        cd emdocs
		
3. Create a new working branch:

        git checkout <branchname>

4. Create a fresh local working branch:

        git pull origin master:<branchname>

5. Create your new article or make changes to an existing article. Use Atom (http://atom.io) as your Markdown editor (or another editor you prefer) to create and open new Markdown files. After you created or modified your article and images, go to the next step.

6. Add and commit any new files you created:

        git add <file path>
        git commit –m "<comment>"
        
   Or, to commit only the specific files you modified:

        git commit -a –m "<comment>"

7. Let your origin know you created the local working branch:

        git push origin <branchname>

8. Push the changes to your 
9.  on GitHub:

        git push origin <branchname>

9. When you are ready to submit your content to the upstream master branch for staging, validation, and/or publishing, in the GitHub UI, create a pull request from your branch to the master branch.

10. The pull request recipient reviews your pull request, provides feedback, and/or accepts your pull request. 

11. Optionally verify your published article or changes at
<span style="color:red;">Need correct URL for viewing published articles.</span>
 http://docs.microsoft.com/ems/articles/name-of-your-article-without-the-MD-extension

<!-- This section probably needs to be removed entirely.
**Notes:**
<span style="color:red;">->> **Do we want to state a schedule?**  <<-</span>

- At this time, technical articles are published once daily around 10 AM Pacific Standard Time (PST), Monday-Friday. Remember, your pull request has to be accepted before changes are included in the next scheduled publishing run.
-->
