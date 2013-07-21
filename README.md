codeInt.tmbundle
================

A (very) simple Textmate bundle for coding and searching interview transcripts.

Introduction
------------
This bundle provides some simple tools for coding interview transcripts, and looking up codes in a batch of transcripts.  It was originally created for TextMate 1.5.10, but has limited functionality in TextMate 2.  It will eventually be converted to a Sublime Text package.

Syntax
------

There are two elements to the syntax: metadata headers and tags

####Metadata  
Metadata must appear as a header at the top of any cInt file.  This follows the format:

`<respondent>: respondent 00`   
`<interview>: interview 00`  
`<date>: YYYY-MM-DD)`  

This metadata allows the search function to attribute codes and content to a given respondent/interview.


####Tags
Inline tags appear in double brackets, followed immediately by the associated interview content in curly brackets.  Multiple tags can be assigned to a single passage if separated by a comma.  For instance:

`[[tag one, tag two]]{Interview content associated with tag one and tag two.}`

Commands
--------

**Tag Quote:** `CMD + {`  
Select the content you wish to code, then use this command to add tags


**Search for Code:** `CMD + SHIFT + K`  
Searches current directory, and returns all content tagged with a given code.  Search is case-sensitive. Respondent name and interview number are included for each content passage returned.

**List Codes:** `CMD + SHIFT + C` (current file), `CMD + SHIFT + OPT + C` (current directory)  
This returns a list of all codes used, either in the current file, or the entire directory of transcripts.

**Insert Metadata:** `CMD + SHIFT + H`  
This inserts a template of metadata at the current cursor location. Note that metadata should appear at the top of the file, however.

Notes
-----
* Files must include metadata headers for search and list commands to work properly.
* Directory-wide searches require that all files in the directory be in cInt format, with proper metadata headers.  Files not following this format (including invisible files) will cause errors (see "Known Issues" section below).

Known Issues
------------
* Commands requiring input do not work in TM2.  This is because TM2 does not include cocoadialog, and I haven't bothered looking into the new method for raw input.
* Directory-wide commands will fail if the directory contains subdirectories or invisible files (e.g., .DS_Store).  I'm sure this is easy to fix.
* Search function is case-sensitive, and probably doesn't need to be.
