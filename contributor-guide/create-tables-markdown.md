<properties
	title="Create tables in markdown"
	pageTitle="Create tables in markdown for EMS articles"
	description="Explains how to code tables in markdown."
	metaKeywords=""
	services=""
	solutions=""
	documentationCenter=""
	authors="v-jocgar"
	videoId=""
	scriptId=""
	manager="robmazz" />

<tags
	ms.service="contributor-guide"
	ms.devlang=""
	ms.topic="article"
	ms.tgt_pltfrm=""
	ms.workload=""
	ms.date="02/19/2016"
	ms.author="v-jocgar" />

# Create tables in markdown

To Do:
- [ ] Add Note syntax to the Note below.
- [ ]
- [ ]   

Tables in articles should be used sparingly. Only use them if the data is truly tabular.

**Note**
Markdown tables are limited in their ability to handle lengthy strings of text; there is no concept of word-wrap within a table cell. A cell will simply expand to the full width of the content, which makes viewing the table on smaller screens somewhat challenging. Use tables for smaller sets of information, and find other meaningful ways to display longer sets of content.

## Markdown table syntax
The simplest way to create a table in markdown is to use pipes and hyphens. You need at least 3 hyphens in the second row for each column to create the table header. Table header text automatically centers and renders as bold text.  

 ![1]

Markdown automatically renders the alternate table row shading.  
 ![2]

You can justify the columns with colons:

    |:-----|   - this is left aligned (default -- can be omitted)
    |-----:|   - this is right aligned
    |:-----:|  - this is centered

The outer pipes are optional, and you don't have to perfectly align the text and pipes for your table to render correctly. This example of quick formatting:

 ![3]

is read and rendered correctly by Markdown.  
 ![4]

If you use HTML tables and your Markdown is not rendering between the two tables, you need to add a closing BR tag after the closing TABLE tag.

![5]

For a quick and easy way to create tables in markdown, try the Markdown tables generator: http://www.tablesgenerator.com/markdown_tables

<!--
- https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#wiki-tables
- http://michelf.ca/projects/php-markdown/extra/#table
-->

## Back to Home

- [Overview article](./../README.md)
- [Index of guidance articles](./contributor-guide-index.md)

<!--image references-->
[1]: ./media/table-markdown-1.png
[2]: ./media/table-markdown-2.png
[3]: ./media/table-markdown-3.png
[4]: ./media/table-markdown-4.png
[5]: ./media/break-tables.png
