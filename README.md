# Election Analysis
In this project, an election results which is given in a csv document are being analized by using Python.
## Overview of Election Audit
The analysis was made to find out total number of votes, the number of votes and their percentages in each county, the counthy with the highest turnout, the vote for each candidate and its persentage and finally the winning conditate with number of votes and its percentage are found out from the document![election_resulsts.csv](.\election_results.csv). To accomplish to this work,several for loops and conditional statemnets were used in python.

The results were prented in commend line (terminal, displayed in this work as png documnet), and they are saved in a text file which is named ![election_results.txt](.\election_results.txt).

In the report the purpose of the project is written; the main points of script are explained; the result is displayed by a figure.The result is broken down in to parts and each part is shown by a table. Finally, a summary statement is icluded, providing a business proposal to the election commission on how this script can be used, with some modifications,for any election.

### Purpose
 The purpuse of the work is to create a python script to make analysis of an election, which is applicable to any election results, independent of number of votes, number of counties and number of candidates. 

## Analysis of Script through Election Audit Results And Challenges

### Analysis of Script through Audit Results
The script contain a main for loop which goes through all rows in the csv document. Before starting the loop, the librories csv and os are imprted to use their functions by
>import csv
>import os
The cvs document loaded to read by 
>THIS_FOLDER = os.path.dirname(os.path.abspath(__file__))
>file_to_load = os.path.join(THIS_FOLDER, "Resources", 'election_results.csv')
A txt document is created to save the results by
>file_to_save = os.path.join(THIS_FOLDER,"analysis","election_results.txt")

### Challenges 



## Election Audit Summary
