---
layout: post
title: "Splunk app deconstruction"
date: 2015-11-18 20:10
comments: false
categories: splunk regex
---

Splunk apps can be a mixed bag.  There's not a definitive style guide, and finding the right line in a savedsearch.conf or transforms.conf can be occasionally frustrating.

A quick and dirty way to find the lines of interest in an app:

```shell
cd /opt/splunk/etc/apps/SA-something/
find . -type f | xargs -I{} grep "your_query_here" {} /dev/null
```
This will print all lines from all files matching your_query_here -- with corresponding filenames and paths.

You're probably thinking, "well duh, that's what grep does", and that's true.  The nifty part of this is that by appending /dev/null to the query you'll also get the filename and path your query appears in, rather than an anonymous list of lines.

This isn't Splunk-specific, it just happens to be handy for it.  It works just as well on Snort configs, or anything else where you might have a line of interest buried in a directory of files. 
