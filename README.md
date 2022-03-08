# Election Analysis
In this project, an election results which is given in a csv document are being analyzed by using Python.
## Overview of Election Audit
The analysis was made to find out total number of votes, the number of votes and their percentages in each county, the county with the highest turnout, the number of votes for each candidate and its persentage and finally the winning candidate with number of votes and its percentage are found out from the document![election_resulsts.csv](.\election_results.csv). To accomplish to this work,several for loops and conditional statemnets were used in python.

The results were printed in commend line (terminal, displayed in this work as png documnet), and they are saved in a text file which is named ![election_results.txt](.\election_results.txt).

In the report the purpose of the project is written; the main points of script are explained; the result is displayed by a figure.The result is broken down in to parts and each part is shown by a table. Finally, a summary statement is icluded, providing a business proposal to the election commission on how this script can be used, with some modifications,for any election.

### Purpose
 The purpuse of the work is to create a python script to make analysis of an election, which is applicable to any election results, independent of number of votes, number of counties and number of candidates. 

## Analysis of Script through Election Audit Results And Challenges

### Analysis of Script through Audit Results
The script contains a main for loop which goes through all rows in the csv document. Before starting the loop, the libraries csv and os are imported to use their functions by

>import csv
>
>import os

The cvs document loaded to read by 

>THIS_FOLDER = os.path.dirname(os.path.abspath(__file__))

>file_to_load = os.path.join(THIS_FOLDER, "Resources", 'election_results.csv')

A txt document is created to save the results by

>file_to_save = os.path.join(THIS_FOLDER,"analysis","election_results.txt")

Some variables as integers,foats, lists and dictionaries are defined and initialized.

The results are printed in the command line (terminal). They are displayed in the following screen shot:

![](https://github.com/dcaliskan777/Election-analysis/blob/main/election_results_in_terminal.png)

The main findings are the total number of votes were cast in this congressional election,the number of votes and the percentage of total votes for each county in the precinct, county which had the largest number of votes, the number of votes and the percentage of the total votes each candidate received, winning candidate and the number of votes and the percentage of votes that condidate recieved. Let's take a closer look to these five results.

#### 1. The total number of votes were cast in this congressional election

In order to find total number of votes the integer variable total_vote was defined and initialized as 

> total_votes = 0

out of the main for loop. At the beginning of inside of the for loop it is inreased by 1 in order to count every vote as

>  total_votes = total_votes + 1

When the loop has ended the total vote was printed in the command line (terminal )and save in the text file as

    with open(file_to_save,"w") as txt_file:    
    election_results = (
        f"\nElection Results:\n\n"
        f"-------------------------\n"
        f"Total Votes: {total_votes:,}\n"
        f"-------------------------\n\n"
        f"County Votes:\n\n")
    print(election_results, end="")

    txt_file.write(election_results)

The total number of votes is

> 369,711

#### 2. The number of votes and the percentage of total votes for each county

In each iteration of the main for loop we check if the county name does not exist in the the list of counties (county_options), if it does not exist we add it to the list and initialize its votes in the county_votes dictionary; otherwise (if the county exists in the list of counties) the value (the number of votes) of current county is increased by 1. These are done by the following part of script:
             
        if county_name not in county_options:

           county_options.append(county_name)

           county_votes[county_name] = 0

        county_votes[county_name] += 1

Note that the last statement is out of if loop. When the main for loop ended the list of county_options (which contains county names) and the dictionary of county_votes (which contais county names as key and the number of votes of corresponding county as value) are created.

In the following part of the script, percentage votes of each county is calculated, by the help of f-formatting the county_results is created, it is printed in command line (terminal) and it is saved in text document.
    
    for county_name in county_votes:  
        votes = county_votes.get(county_name) 
        vote_percentage = float(votes) / float(total_votes) * 100
        county_results = (
            f"{county_name}: {vote_percentage:.1f}% ({votes:,})\n")

        print(county_results)
       
        txt_file.write(county_results)

The output can be summarized in the following table:

| Name of the county    | The number of votes  | The percentage of votes|
|:-----:                | :-----:              |:-----:                 |
| Jefferson             | 38,855               | 10.5%                  | 
| Denver                | 306,055              | 81.8%                  |
| Arapahoe              | 24,801               | 6.7%                   |
| **The Total**         | 369,711              | 100%                   |

#### 3. County which had the largest number of votes

In order to determine the county which had the highest number of votes we a variable before starting the main for loop, named largest_count and we assigned 0 for it initially. And then in the for loop of counties we compare it with the votes, if votes is larger than largest_count then votes is assigned to largest_count. This comparison provids to determine also corresponding county name and percentage of votes. This is being done by the following part of the script:
txt_file.write(county_results)

        
        if votes > largest_count:
            largest_count = votes
            largest_county = county_name
            largest_percentage = vote_percentag
            
 The following codes are for printing and saving, the result of the county which had the highest number of votes.
 
    largest_county_results=(
        f"        \n"
        f"----------------------\n"
        f"The county with the highest turnout : {largest_county} \n"
        f"The number of votes in that county  : {largest_count:,} \n"
        f"Percentage of the votes             : {largest_percentage:.1f}% \n"
        f"----------------------\n\n"
        f"Candidate results:\n\n")
    print(largest_county_results)
 
    txt_file.write(largest_county_results)
 
 The output can be summarized in the following table:
 | Name of the county with the highest turnout    | The number of votes  | The percentage of votes|
|:-----:                                          | :-----:              |:-----:                 |
| Denver                                          | 306,055              | 82.8%                  | 

#### 4. The number of votes and the percentage of the total votes each candidate received

In each iteration of the main for loop we check if the candidate name does not exist in the the list of candidates (candidate_options), if it does not exist we add it to the list and initialize its votes in the candidate_votes dictionary; otherwise (if the candidate exists in the list of candidate) the value (the number of votes) of current candidate is increased by 1. These are done by the following part of script:


       
        if candidate_name not in candidate_options:

            candidate_options.append(candidate_name)

            candidate_votes[candidate_name] = 0

        candidate_votes[candidate_name] += 1
        
Note that the last statement is out of if loop. When the main for loop ended the list of coandidate_options (which contains candidate names) and the dictionary of candidate_votes (which contais candidate names as key and the number of votes of corresponding candidate as value) are created.

In the following part of the script, percentage votes of each candidate is calculated, by the help of f-formatting the candidate_results is created, it is printed in command line (terminal) and it is saved in text document.

# 8: Save the county with the largest turnout to a text file.
   
    for candidate_name in candidate_votes:

        votes = candidate_votes.get(candidate_name)
        vote_percentage = float(votes) / float(total_votes) * 100
        candidate_results = (
            f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")

        print(candidate_results)
   
        txt_file.write(candidate_results)
        
The output can be summarized in the following table:

| Name of the candidate     | The number of votes  | The percentage of votes|
|:-----:                    | :-----:              |:-----:                 |
| Charles Casper Stockham   | 85,213               | 23.0%                  | 
| Diana DeGette             | 272,892              | 73.8%                  |
|Raymon Anthony Doane       | 11,606               | 3.1%                   |
| **The Total**             | 369,711              | 99.9%                  |

The percentage of total votes is unexpectedly 99.9%. It is due to the ignored part of percentages when thwy are rounding.
It means the some of ihnored parts of percentages is 0.01%.
        
#### 5. Winning candidate and the number of votes and the percentage of votes that condidate recieved
## Election Audit Summary
