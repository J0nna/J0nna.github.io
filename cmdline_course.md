---
layout: default
---
## Command line tools for linguists

This course gives a student the basic knowledge of how to operate Unix-like command line environments. It focuses especially on functions that are useful for linguists.

According to the course description on [WebOodi](https://weboodi.helsinki.fi/hy/opettaptied.jsp?MD5avain=cd20e682-4d26-47f7-81e0-4dcd16ccee9e&Kieli=1&OpetTap=129824412&takaisin=omatopinn.jsp&NaytIlm=1&NaytSuor=0&NaytSuun=0&NaytHyl=0), the students who take this course learn to:
* operate in a Unix-like environment.
* use Unix command-line on a Windows or Mac OSX computer.
* use the Unix command-line.
* use regular expressions.
* processing corpora at a basic level.
* run programs from the command-line.
* install programs.
* write basic scripts.
* use version control tools.
* work on a remote server.
* create and host a webpage on GitHub Pages.
* _and most importantly_ stay calm and google when things go wrong.

#### Week 1

##### Introduction to Command Line Environments

The first week of the course was about a brief theoretical introduction to command line, computer architecture and operating systems, setting up the command line environments on students' personal computers and learning the first basic commands.

The most used basic commands I learned during the first week:

| Command  | Function                      |
| -------- |:-----------------------------:|
| cd       | changes directory             |
| ls       | lists contents of a directory |
| less     | views a file                  |
| emacs    | opens emacs                   |

#### Week 2

##### Navigating a UNIX System

During the second week of the course we learned to navigate around the Unix system copying, moving and deleting directories and compressing files. We connected to a remote server for the first time.

> In my opinion this was the most difficult week of the course. 

#### Week 3

##### Basic Corpus Processing

Week 3 of the course taught us about the encoding systems and basic corpus processing. We learned, for example, to remove duplicate lines from a text file and to count words, characters or lines.

The command to count words, characters and lines from a textfile:

```wc <filename>```

#### Week 4

##### Advanced Corpus Processing

During the 4th week of the course we continued with the corpus processing. The most important things we learned were to generate frequency lists and n-grams.

> This was probably the most important week for all (future) linguists.

#### Week 5

##### Scripting and Configuration Files

We learned to modify existing scripts and to write some basic scripts ourselves.  

> I really liked writing scripts by myself during the quiz 5!

One of the scripts I wrote. It returns a comparative form of an english adjective the user has given:

```python

#!/bin/bash

# script: comparative.sh
# author: Jonna Tarvainen

# This script gives the comparative form of the english adjective the user gives as a parameter. Does not work for the adjectives with a comparative form formed with "more" or irregular adjectives such as "good-better-the best".

str=$1

if [ "${str: -1}" == "e" ]
then
    echo "${str}""r"
    elif [ "${str: -1}" == "y" ]
    then
        echo "${str::-1}""ier"
	else
	    echo "${str}""er"
	    fi
```

#### Week 6

##### Installing and Running Programs

This week we studied different ways of installing programs, softwares and packages. The use of sudo and other installation commands were explained. Also, we wrote our first Makefiles.

One of the Makefile versions from this course week:

```python
BOOKS=alice christmas_carol dracula frankenstein heart_of_darkness life_of_bee moby_dick modest_propsal pride_and_preju\
dice tale_of_two_cities ulysses

FREQLISTS=$(BOOKS:%=results/%.freq.txt)
SENTEDBOOKS=$(BOOKS:%=results/%.sent.txt)
#ALLNOMD=$(BOOKS:%=data/all.no_md.txt)

all: $(FREQLISTS) $(SENTEDBOOKS)

#clean:
#       rm -f results/* data/*no_md.txt

%.no_md.txt: %.txt
        python3 src/remove_gutenberg_metadata.py $< $@

results/%.freq.txt: data/%.no_md.txt
        src/freqlist.sh $< $@

results/%.sent.txt: data/%.no_md.txt
        src/sent_per_line.sh $< $@

#data/all.no_md.txt: data/%.no_md.txt
#       cat $^ $@
```

#### Week 7

##### Version Control

During the 7th week we set up Github accounts and learned a lot about the vesion control and the importance of it in developing projects.


<img src="assets/images/myaccount.jpg" alt="Photo" hspace="20" width="100%" align="right"/>

We learned to use the following commands:

```git add .```

```git commit```

```git push```

We also checked how to undo the changes.

#### Final assignment

For the final assignment of this course we created these websites by using Git.

The most used command during the final assignment project was `bundle exec jekyll serve`.