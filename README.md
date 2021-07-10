# Election_Analysis
A Colorado Board of Elections employee has given you the following tasks to complete the election audit of a recent local congressional election.

1. Calculate the total number of votes cast.
2. Get a complete list of candidates who received votes.
3. Calculate the total number of votes each candidate received.
4. Calculate the percentage of votes each candidate won.
5. Determine the winner of the election based on popular vote.

## Resources
- Data Source: election_results.csv
- Software: Python 3.7.6, Visual Studio Code 1.58.0

## Summary
The analysis of the election shows that:
- There were 369,711 votes cast in the election.
- The candidates were:
  - Charles Casper Stockham
  - Diana DeGette
  - Raymon Anthony Doan
- The candidate results were:
   - Charles Casper Stockham received 23% of the vote and 85,213 votes.
   - Diana DeGette received 73.8% of the vote and 272,892 votes.
   - Raymon Anthony Doane received 3.1% of the vote and 11,606 votes.
- The winner of the election was Diana DeGette, who received 73.8% of the vote and 272,892 votes. 

## Challenge  Overview
Tom, the client, asked for assistance with an election audit of the tabulated results for a US congressional precinct in Colorado. The goal of the audit was to to generate a vote count report to certify the race. This audit is ususally done in Excel. However, Seth (Tom's manager) asked if there was a way to automate the process using Python. Seth clarified that if the audit was successfully performed with Python, the program code could be used to audit other congressional and senatorial districts. The code would also be used for reporting local elections. 

#### Voting Methods
There were three primary voting methods for the election, which were as follows:
- Mail in ballots, which are typically counted in the central office.
- Punch cards, which are collected and fed into a machine that tabulates vote totals and sends the results to the centeral office.
- Direct recording electronic (DRE) counting machines are sent to the central office and read by a computer.

Findings were requested for:
- The total number of that were votes cast.
- The total number of votes for each candidate.
- The percentage of votes for each candidate.
- The winner of the election based on the popular vote.
- The voter turnout for each county
- The percentage of votes from each county
- The percentage fo votes from each county out of the total count
- The county with the highest turnout.

## Election Audit Results
The election audit findings for bullet points 1-4 are listed in the Summary section above. The voting results at the county level were:
-


## Challenge Summary
The project files and python code were stored in a GitHub repository. Some of the benefits of using the repository for projects are:
- Easy access by multiple contributors.
- Versioning, to prevent files and scripts from accidently being overwritten. 
- Security to prevent others from corrupting the project files. 
The Python script for the audit was written and run in an application called Visual Studio (VS) Code. 
Some of the advantages of using VS code instead of the Python interpreter are:
- Errors are easy to spot and correct.
- Views of editor and terminal can be easily configured.
- Multiple tips and autocomplete functions are available.
- The VS Code test editor provides useres with notification of syntax errors and misspellings.
- The application is easy to integrate with GitHub.
The Python algorithm for the report included:
- Lists and dictionaries with indexes
- Decision, print, repetition(loop)statements
- If and with statements
- Membership and logical operators
- Single and multi-line f strings
- Dependencies for csv and os 
- Pseudo code to explain funtion and purpose. 
