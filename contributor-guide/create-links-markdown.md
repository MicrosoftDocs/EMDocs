<properties
   pageTitle="Create links in markdown articles" description="Explains how to code crosslinks in markdown." metaKeywords="" services="" solutions="" documentationCenter="" authors="tysonn" videoId="" scriptId="" manager="carolz" />

<tags ms.service="contributor-guide" ms.devlang="" ms.topic="article" ms.tgt_pltfrm="" ms.workload="" ms.date="02/03/2015" ms.author="tysonn" />

# Linking guidance for Azure technical content
To Do: 
- [ ] Confirm EMS article repo layout for links
- [ ] Find the URL to the EMS documentation and incorporate
- [ ] Confirm whether we're allowing use of FWLinks at all
- [ ] 
- [ ]  
- [ ] 
- [ ] 
- [ ]   

## Guidelines for technical articles on ems.microsoft.com

| Link scenario | Guidance for the target link  |
|---------------|-----------|
|Linking from an EMS technical article to another EMS technical article|Use relative links.|
|Linking to an EMS page outside the documentation directory, to an MSDN library topic, a TechNet library topic, or to a KB article|​Use the actual link to the article or topic. Remove the en-us language locale from the link.|
|Linking from an EMS article to any other web page|Use the direct link|

### Use friendly link text

The words you include in a link should be friendly - in other words, they should be normal English words or the title of the page you are linking to. Do not use "click here". It's bad for SEO and doesn't adequately describe the target.

**Correct:**

- `For more information, see the [contributor guide index](https://github.com/Azure/azure-content/blob/master/contributor-guide/contributor-guide-index.md).`

- `For more details, see the [SET TRANSACTION ISOLATION LEVEL](https://msdn.microsoft.com/library/ms173763.aspx) reference.`

**Incorrect:**

- `For more details, see [https://msdn.microsoft.com/library/ms173763.aspx](https://msdn.microsoft.com/library/ms173763.aspx).`

- `For more information, click [here](https://github.com/Azure/azure-content/blob/master/contributor-guide/contributor-guide-index.md).`

### Markdown syntax for EMS relative links

To create an inline link from an EMS technical article to another EMS technical article, use this link format. If you create any new links to or from articles in the directories, you’ll need to follow the new linking syntax.

Old link syntax to link from one EMS tech doc to another:

    [link text](filename.md)

**New link syntax** 

Article links from a subdirectory to an article in the root directory:

    [link text](../article-name.md)

Article in the root directory links to an article in a service subdirectory: 

    [link text](service-directory/article-name.md)

Article in a service subdirectory links to an article that is in another service subdirectory:

    [link text](../service-directory/article-name.md)
 
Article in a directory links to another article in the same directory:

    [link text](article-name.md)


You do not have to create anchors anymore - they are automatically generated at publishing time for all H2 headings. The only thing you have to do is create links to the H2 sections:

    [link](#the-text-of-the-H2-section-separated-by-hyphens)
    [Create cache](#create-cache)

To link to an anchor in another article in the same subdirectory:

    [link text](article-name.md#anchor-name)
    [Configure your profile](media-services-create-account.md#configure-your-profile)

To link to an anchor in another service subdirectory:

    [link text](service-directory/article-name.md#anchor-name)
    [Configure your profile](service-directory/media-services-create-account.md#configure-your-profile)


## Custom markdown link syntax

Since includes files are located in another directory, you will need to use relative paths as below. For a link to a single article from an includes file, use this format:

    [link text](../articles/service-folder/article-name.md)
    
Learn more about how to use an includes file in the [Custom markdown extensions guidelines](custom-markdown-extensions.md#includes).

If you have selectors embedded in an include, you would use this sort of linking: 

    > [EMS.SELECTOR-LIST (Dropdown1 | Dropdown2 )]
    - [(Text1 | Example1 )](../articles/service-folder/article-name1.md)
    - [(Text1 | Example2 )](../articles/service-folder/article-name2.md)
    - [(Text2 | Example3 )](../articles/service-folder/article-name3.md)
    - [(Text2 | Example4 )](../articles/service-folder/article-name4.md)

To link to a page on EMS (such as a pricing page, a Service Level Agreement page, or anything else that is not a documentation article), use an absolute URL, but omit the locale. The goal here is that links work in GitHub and on the rendered site:

    [link text](http://azure.microsoft.com/pricing/details/virtual-machines/)

To test your links, push your page to your fork and view it in the rendered view and publish to Sandbox. The cross links on the GitHub version of the page should work as long as the targets of the URLs are present in your fork.

## Reference-style links

You can use reference style links to make your source content easier to read. The reference style links replace the inline link syntax with simplified syntax that allows you to move the long URLs to the end of the article. Here's Daring Fireball's example:

Inline text:

    I get 10 times more traffic from [Google][1] than from [Yahoo][2] or [MSN][3].

Link references at the end of the article:

    <!--Reference links in article-->
    [1]: http://google.com/
    [2]: http://search.yahoo.com/  
    [3]: http://search.msn.com/

## FWLinks

Avoid FWLinks (our redirection system) in https://www.microsoft.com/en-us/server-cloud/enterprise-mobility content. They should be used only as a last resort when you need to create a link for a page whose URL you don't yet know. They are almost never actually needed. For EMS, you define the file name, so you can know what it will be ahead of time. For a library topic that is not yet published, you can create a link that uses the topic GUID so that you don't have to use an FWLink.

If you must use an FWLink on a web page, include the P parameter to make it a permanent redirect:

    http://go.microsoft.com/fwlink/p/?LinkId=389595

When you paste the target URL into the FWLink tool, remember to remove the locale if your target link is EMS, or the MSDN or TechNet library.

## Additional Reading

- [Overview article](./../README.md)
- [Index of guidance articles](./contributor-guide-index.md)

<!--image references-->
[1]: ./media/create-tables-markdown/table-markdown.png
[2]: ./media/create-tables-markdown/break-tables.png
