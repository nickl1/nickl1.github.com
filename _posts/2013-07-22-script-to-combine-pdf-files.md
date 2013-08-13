---
layout: post
title: "script to combine pdf files"
category: posts
---


> a python script to combine pdf files together, based on sort option


I download some pdf files online, they are seperated pieces from a ebook,  I need to combine them togehter to make the book as a whole.

There are lots method to combine, but in Mac I found preview is not handy, and **join.py** is the default script in Mac to do the trick, it is located at */System/Library/Automator/Combine PDF pages.action/Contents/Resources/join.py*

I need to combine all the pdf in a folder based on time ascending order, I found a [script](http://jasonmaur.com/merge-pdf-files-using-python/) but it does not have what I need, so I decided to write one.

Here it is 

#### source

[source](https://github.com/airbob/personal-backup/blob/master/scripts/mergepdf/merge.py)

[ReadMe](https://github.com/airbob/personal-backup/blob/master/scripts/mergepdf/ReadMe.md)




#### functions

Merge pages from a a collection of PDF files into a single PDF file.

#### usage

<pre><code>
   ./mergepdf.py [--path  <path containing pdf files to merge>]  [--sort <sort the pdf files in source directory by: name/date asc/decending order>]  [--output] [--output path and file name]"
</code></pre>

#### example usage

<pre><code>
./mergepdf.py --path ~/Desktop/test/ --sort nameasc --output ~/Desktop/merge.pdf
</code></pre>