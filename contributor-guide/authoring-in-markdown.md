<properties
    pageTitle="Authoring in Markdown"
    description="Explains how to create images in markdown according to guidelines set for the Enterprise Mobility Suite repositories."
    services=""
    solutions=""
    documentationCenter=""
    authors="v-jocgar"
    manager="robmazz"
    editor="v-jocgar"/>

<tags
    ms.service="contributor-guide"
    ms.devlang=""
    ms.topic="article"
    ms.tgt_pltfrm=""
    ms.workload=""
    ms.date="02/17/2016"
    ms.author="v-jocgar" />

#Authoring in Markdown


## Create images in markdown

### Image folder creation and link syntax

For a new article, you'll need to create a folder in the following location:

    /articles/<service-directory>/media/<article-name>/

For example:

    /articles/app-service/media/app-service-enterprise-multichannel-apps/

After you create the folder and added images to it, use the following syntax to create images in your article:

```
![Alt image text](./media/article-name/your-image-filename.png)
```
Example:

See [the markdown template](../markdown%20templates/markdown-template-for-new-articles.md) for an example.  The image reference links in this markdown template are designed to be at the bottom of the template.

## Guidelines specific to Enterprise Mobility Suite

Screenshots are currently encouraged if it's not possible to include repro steps. Do write your content so that the content can stand without the screenshots if necessary.

Use the following guidelines when creating and including art files:
- Do not share art files across documents. Copy the file you need and add it to the media folder for your specific topic. Sharing between files is discouraged because  it is easier to remove deprecated content and images which keeps the repo clean.

- .png files are highly preferred over other formats.

- Use red squares of the default width provided in Paint (5 px) to call attention to particular elements in screenshots.  

    Example:
    
    ![This is an example of a red square used as a callout.](./media/create-images-markdown/gs13noauth.png)

- Avoid whitespace on edges of screenshots. If you crop a screenshot in a way that leaves white background at the edges, add a single pixel gray border around the image.  If using Paint, use the lighter gray in the default color pallete (0xC3C3C3). If using some other graphic app, the RGB color is R195, G195, 195. You can easily add a gray border around an image in Visio--to do this, select the image, select Line, and ensure the the correct color is set, and then change the line weight to 1 1/2 pt.  Screenshots should have a 1-pixel-wide gray border so that white areas of the screenshot do not blur into the web page.

    Example:

    ![This is an example of a gray border around whitespace.](./media/create-images-markdown/agent.png)

- Conceptual images with whitespace do not need a gray border.  
    
    Example:

    ![This is an example of a conceptual image with whitespace and no gray border.](./media/create-images-markdown/ic727360.png)

- Try not to make an image too wide.  Images will be automatically resized if they are too wide. However, the resizing sometimes causes fuzziness, so we recommend that you limit the width of your images to 780 px, and manually resize images before submission if necessary.

- Show command outputs in screenshots.  If your article includes steps where the user is working within a shell, it's useful to show command output in screenshots. In this case, restricting your shell width to about 72 characters generally ensures that your image will remain within the 780 px width guideline. Before taking a screenshot of output, resize the window so that just the relevant command and output is shown (optionally with a blank line on either side).

- Take whole screenshots of windows when possible. When taking a screenshot of a browser window, resize your browser window to 780 px wide or less, and keep the height of the browser window as short as possible such that your application fits within the window.

    Example:

    ![This is an example of a browser window screenshot.](./media/create-images-markdown/helloworldlocal.png)

- Use caution with what information is revealed in screenshots.  Do not reveal internal company information or personal information.

- In conceptual art or diagrams, use the official icons in the Cloud and Enterprise symbol and icon set. A public set is available at http://aka.ms/CnESymbols.

# Linking guidance for Azure technical content
## Guidelines for technical articles on azure.microsoft.com

| Link scenario | Guidance for the target link  |
|---------------|-----------|
|Linking from an ACOM technical article to another ACOM technical article|Use relative links.|
|Linking to an ACOM page outside the documentation directory, to an MSDN library topic, a TechNet library topic, or to a KB article|​Use the actual link to the article or topic. Remove the en-us language locale from the link.|
|Linking from an ACOM article to any other web page|Use the direct link|

### Use friendly link text

The words you include in a link should be friendly - in other words, they should be normal English words or the title of the page you are linking to. Do not use "click here". It's bad for SEO and doesn't adequately describe the target.

**Correct:**

- `For more information, see the [contributor guide index](https://github.com/Azure/azure-content/blob/master/contributor-guide/contributor-guide-index.md).`

- `For more details, see the [SET TRANSACTION ISOLATION LEVEL](https://msdn.microsoft.com/library/ms173763.aspx) reference.`

**Incorrect:**

- `For more details, see [https://msdn.microsoft.com/library/ms173763.aspx](https://msdn.microsoft.com/library/ms173763.aspx).`

- `For more information, click [here](https://github.com/Azure/azure-content/blob/master/contributor-guide/contributor-guide-index.md).`

### Markdown syntax for ACOM relative links

To create an inline link from an ACOM technical article to another ACOM technical article, use this link format.   If you create any new links to or from articles in the directories, you’ll need to follow the new linking syntax.

Old link syntax to link from one ACOM tech doc to another:

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

    > [AZURE.SELECTOR-LIST (Dropdown1 | Dropdown2 )]
    - [(Text1 | Example1 )](../articles/service-folder/article-name1.md)
    - [(Text1 | Example2 )](../articles/service-folder/article-name2.md)
    - [(Text2 | Example3 )](../articles/service-folder/article-name3.md)
    - [(Text2 | Example4 )](../articles/service-folder/article-name4.md)

To link to a page on ACOM (such as a pricing page, SLA page or anything else that is not a documentation article), use an absolute URL, but omit the locale. The goal here is that links work in GitHub and on the rendered site:

    [link text](http://azure.microsoft.com/pricing/details/virtual-machines/)

To test your links, push your page to your fork and view it in the rendered view and publish to Sandbox. The cross links on the GitHub version of the page should work as long as the targets of the URLs are present in your fork.

Our [markdown template for technical articles](../markdown templates/markdown-template-for-new-articles.md/) shows an alternate way to create crosslinks in markdown so all the crosslinks are coded together at the end of the article, even while they display inline.

## Reference-style links

You can use reference style links to make your source content easier to read. The reference style links replace the inline link syntax with simplified syntax that allows you to move the long URLs to the end of the article. Here's Daring Fireball's example:

Inline text:

    I get 10 times more traffic from [Google][1] than from [Yahoo][2] or [MSN][3].

Link references at the end of the article:

    <!--Reference links in article-->
    [1]: http://google.com/
    [2]: http://search.yahoo.com/  
    [3]: http://search.msn.com/

## Remember the Azure library chrome!
If you want to link to an Azure library topic that lives under [this node](https://msdn.microsoft.com/library/azure), remember to specify the Azure chrome in the link (/azure/). The Azure chrome shares the ACOM navigation options and displays only the Azure content of the MSDN library. A properly scoped link looks like this:

    http://msdn.microsoft.com/library/azure/dd163896.aspx

Otherwise, the page will be rendered in the standard MSDN view, with the entire MSDN tree displayed.

## FWLinks

Avoid FWLinks (our redirection system) in azure.microsoft.com content. They should be used only as a last resort when you need to create a link for a page whose URL you don't yet know. They are almost never actually needed. For ACOM, you define the file name, so you can know what it will be ahead of time. For a library topic that is not yet published, you can create a link that uses the topic GUID so that you don't have to use an FWLink.

If you must use an FWLink on a web page, include the P parameter to make it a permanent redirect:

    http://go.microsoft.com/fwlink/p/?LinkId=389595

When you paste the target URL into the FWLink tool, remember to remove the locale if your target link is ACOM, or the MSDN or TechNet library.

### Contributors' Guide Links

- [Overview article](./../README.md)
- [Index of guidance articles](./contributor-guide-index.md)

<!--image references-->
[1]: ./media/create-tables-markdown/table-markdown.png
[2]: ./media/create-tables-markdown/break-tables.png

###Contributors' Guide Links

- [Overview article](./../README.md)
- [Index of guidance articles](./contributor-guide-index.md)

