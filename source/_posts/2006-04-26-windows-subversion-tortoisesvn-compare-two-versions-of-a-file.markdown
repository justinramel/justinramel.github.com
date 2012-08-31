---
comments: true
date: 2006-04-26 13:47:52
layout: post
slug: windows-subversion-tortoisesvn-compare-two-versions-of-a-file
title: Windows SubVersion / TortoiseSVN - Compare two versions of a file
wordpress_id: 70
categories:
- Subversion
---

Today I needed to compare two different versions of a source file.  One in the main trunk folder and the other in a previously tagged version folder. This is easily done in TortoiseSVN, snippet from the TortoiseSVN manual:



> **Compare two revisions of a file**
If you want to compare two revisions in a file's history, for example revisions 100 and 200 of the same file, just use TortoiseSVN => Show Log to list the revision history for that file. Pick the two revisions you want to compare then use Context Menu => Compare Revisions.

If you want to compare the same file in two different trees, for example the trunk and a branch, you can use the repository browser to open up both trees, select the file in both places, then use Context Menu => Compare Revisions.

If you want to compare two trees to see what has changed, for example the trunk and a tagged release, you can use TortoiseSVN => Revision Graph Select the two nodes to compare, then use Context Menu => Compare HEAD Revisions. This will show a list of changed files, and you can then select individual files to view the changes in detail. Alternatively use Context Menu => Unified Diff of HEAD Revisions to see a summary of all differences, with minimal context.




The process of comparing two trees is really nicely done, you get a list of all the files which have been changed between the two trees. You can then drill into this list and see the changes made to individual files. Kewl!
