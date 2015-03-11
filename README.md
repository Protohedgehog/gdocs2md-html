gdocs2Rmd
========

A simple Google Apps script to convert a properly formatted Google Drive Document to the Rmarkdown (.Rmd) format. Fork of the gdocs2md repository — there've been many (180 at time of writing!), and some collation of changes between them could be valuable.

*NB* there's no code change from the markdown version yet. To consider:

* Would this actually be best outputting md or Rmd format?
* What value would code/YAML serve?
   * programmatic access through Google Apps script to write YAML headers based on user input would be a nice way to make Rmarkdown more user-friendly, and perhaps help guide the construction of more elaborate custom knit setups (see post on modular workbooks, linked below).

Related directions:

* [One weird trick to compile multipartite dynamic documents with Rmarkdown](http://biochemistri.es/one-weird-rmd-trick)
* [A modular Rmarkdown workbook](biochemistri.es/modular-workbook)
* [devnotes: Custom application to open .gdoc extensions](https://github.com/lmmx/devnotes/wiki/Custom-application-to-open-.gdoc-extensions)
* [devnotes: Google drive gdoc download conversion workaround](https://github.com/lmmx/devnotes/wiki/Google-drive-gdoc-download-conversion-workaround)

## To-do list

[See devnotes wiki page](https://github.com/lmmx/devnotes/wiki/gdocs2md-debugging:-repo-network,-round-2#to-do)

## Usage

  * Adding this script to your doc (once per doc):
    * Open your Google Drive document (http://drive.google.com)
    * Tools -> Script Manager > New
    * Select "Blank Project".
    * Clear the myFunction() default empty function and paste the contents of [converttomarkdown.gapps](https://raw.github.com/mangini/gdocs2md/master/converttomarkdown.gapps) into the code editor
    * File -> Save (or `Ctrl`/`⌘` + `S`)
    * When prompted enter new project name for '*Untitled project*', e.g. '*gdocs2Rmd*'
    
  * Running the script (run as many times as you want):
    - Tools > Script Manager
    - Select "ConvertToMarkdown" function.
    - Click Run button (First run will require you to authorize it. Authorize and run again)
    - Converted doc with images attached will be emailed to you. Subject will be "[MARKDOWN_MAKER]...".


## Interpreted formats
  * Text:
    * paragraphs are separated by two newlines
    * text styled as heading 1, 2, 3, etc is converted to Markdown heading: #, ##, ###, etc
    * text formatted with Courier New is backquoted: ``text``
    * links are converted to MD format: `[anchortext](url)`
  * Lists:
    * Numbered lists are converted correctly, including nested lists
    * bullet lists are converted to "`*`" Markdown format appropriately, including nested lists
  * Images:
    * images are correctly extracted and sent as attachments
  * Blocks:
    * Table of contents is replaced by `[[TOC]]`
    * blocks of text delimited by "--- class whateverclassnameyouwant" and "---" are converted to `<div class="whateverclassnameyouwant"></div>` 
    * Source code: 
      * **UPDATED**: blocks of text delimited by "--- source code" or "--- src" and "---" are converted to `<pre></pre>`
      * **NEW**: blocks of text delimited by "--- source pretty" or "--- srcp" and "---" are converted to `<pre class="prettyprint"></pre>`
    * Tables:
      * **NEW**: Simple `<table>` processing
  * "--- jsperf `<testID>`" is replaced by an iframe that shows an interactive chart of a JSPerf test. The `<testID>` is the last part of the URL of the Browserscope anchor in your JSPerf test. Something like `"agt1YS1wcm9maWxlcnINCxIEVGVzdBjlm_EQDA"` in the URL `http://www.browserscope.org/user/tests/table/agt1YS1wcm9maWxlcnINCxIEVGVzdBjlm_EQDA`
 


## CONTRIBUTORS

* Renato Mangini - [G+](//google.com/+renatomangini) - [Github](//github.com/mangini)
* Ed Bacher - [G+](//plus.google.com/106923847899206957842) - [Github](//github.com/evbacher)

## LICENSE

Use this script at your will, on any document you want and for any purpose, commercial or not. 
The MarkDown files generated by this script are not considered derivative work and 
don't require any attribution to the owners of this script. 

If you want to modify and redistribute the script (not the converted documents - those are yours), 
just keep a reference to this repo or to the license info below:

```
Copyright 2013 Google Inc. All Rights Reserved.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
