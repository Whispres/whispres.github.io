---
layout: post
author: R.E. Sprouse
title: Presenting PDFs in the Browser on Jekyll Sites
subtitle: Use Liquid to Simplify File Sharing
category: [Website Design, Simple Solutions, Strategic Problem Solving]
tags: [Jekyll, Liquid, HTML, PDF, code]
---
<p>
My Goal: Create project pages to showcase full PDFs of my portfolio pieces.
</p>
<p>
My solution has to be:
* Jekyll and GitHub Pages compatible
* User friendly and visually appealing
* Quick to implement
* Easy to use and maintain
</p>
<p>
My Solution: Generate PDFs in the website browser from my Jekyll site root
directory using Liquid and HTML to make a project page layout.
</p>

#### Why Present PDFs in the Browser
<p>
Embedding PDFs in webpages provides easy access to content without exposing the
user's computer to risk. Potential malware concerns aside, downloading PDFs from
websites to view documents is tedious and consumes computer resources.
Failing to provide in-browser access to PDFs is a major turnoff for many users
even when interacting with trusted sites.
</p>
<p>
This feature is so important to me as a user it can be the deciding factor on
whether or not I reference a site regardless of content quality. Given I am a
devoted follower of the Golden Rule, I strive to code for others as I would have
others code for me.
</p>

#### HTML Methods to Embed a PDF
<p>
 Embedding a PDF file in a webpage with HTML is relatively easy. I followed
 [this helpful article's](http://jsgyan.blogspot.com/2017/12/how-to-display-pdf-in-html-web-page.html)
 advice closely with a few tweaks to suit my purposes. Using the HTML object,
 embed and iframe methods together reaches the largest number of user. I wrapped
 the methods around an error statement and incorporated the option to download
 the file as a fallback if the browser fails to render the PDF.
</p>

~~~
 <object data="[path to PDF here]" width="600" height="500">
   <embed src="[path to PDF here]"  type="application/pdf" width="600px" height="500px"/>
     <iframe src="[path to PDF here]" style="width:600px; height:500px;">
       <p>This browser does not support PDFs. Please download the PDF to view it:
         <a href="[path to PDF here]">Download PDF</a>.
       </p>
     </iframe>
   </embed>
 </object>
 ~~~
<p>
The path provides the PDF location within the site root directory. For example, `/assets/pdf/example.pdf` would be the path to `example.pdf` and functions as a link
to the PDF.</p>

#### Using Liquid to Create a Layout
<p>The above HTML code works like a dream, but it would be monotonous to copy,
paste and edit the file path for every individual project PDF. Excessive or
repetitive code is also difficult to maintain and can slow down the site.
I want to easily include the PDF in a page where I only need to add the PDF name whenever
I add a new project.

First, I created a new `.html` file under my `_layouts` folder in the root directory.

Second, I created a Liquid iteration, or loop, [tag](https://shopify.github.io/liquid/basics/introduction/) using the [for](http://shopify.github.io/liquid/tags/iteration/) loop.

my PDF file using ['site.static_files'](https://jekyllrb.com/docs/static-files/)
