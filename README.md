## Challenge  Overview - Rough Draft
Tom, the client, asked for assistance with an election audit of the tabulated results for a US congressional precinct in Colorado. The goal of the audit was to generate a vote count report to certify the race. This audit is usually done in Excel. However, Seth (Tom's manager) asked if there was a way to automate the process by using Python. Seth clarified that if the audit was successfully performed with Python, the code could be used to audit other congressional and senatorial districts. The code would also be used for reporting local elections. 

#### Voting Methods
There were three primary voting methods for the election, which were as follows:
- Mail in ballots, which are typically counted in the central office.
- Punch cards, which are collected and fed into a machine that tabulates vote totals and sends the results to the central office.
- Direct recording electronic (DRE) counting machines, which are sent to the central office and read by a computer.

Seth and Tom initially requested audit results for the election candidates. However, after the findings were reviewed they realized that more data was necessary and asked that the county level information be added to the report. The code for the initial report was then repurposed to include the county data.

The report contains the following information, which can be viewed in a text file or printed to the terminal for immedicate viewing: 
- The total number of votes that were cast.
- The total number of votes for each candidate.
- The percentage of votes for each candidate.
- The winner of the election based on the popular vote.
- The voter turnout for each county
- The percentage of votes from each county
- The percentage of votes from each county out of the total count
- The county with the highest turnout.

## Election Audit Results
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

The election counties were:
- Arapahoe
- Denver
- Jefferson

The voting results at the county level were:
- Arapahoe received 6.7% of the total with 24,801 votes
- Denver received 82.8% of the total with 306,055 votes
- Jefferson received 10.5% of the total with 38,855 votes
- The county with the highest voter turnout was Denver, with 306,055 votes.

## Challenge Summary
#### Applications and Alogorithm Overview
The original Python algorithm returned information specific to each candidate. The script was then modified at the request of the client, to retun additional details at the county level. The Python code for each report is in appendix A at the end of this summary.
The project files and python code were stored in a GitHub repository for ease of use. Some of the benefits of using the repository for projects are:
- Easy access by multiple contributors.
- Versioning, to prevent files and scripts from accidently being overwritten. 
- Security to prevent others from corrupting the project files. 

The Python script for the audit was written and run in an application called Visual Studio (VS) Code. 
Some of the advantages of using VS code instead of the Python interpreter are:
- Errors are easy to spot and correct.
- Views of the editor and the terminal can be easily configured.
- Multiple coding tips and autocomplete functions are available.
- The VS Code test editor provides users with notification of syntax errors and misspellings.
- The application is easy to integrate with GitHub.

The Python code for the report is easy to reuse and can be applied to other election audits by basically switching out the variables and modifying some of the with and if statements, loops and f strings.
The Python algorithm for the report included:
- Lists and dictionaries with indexes
- Decision, print, repetition(loop)statements
- If and with statements
- Membership and logical operators
- Single and multi-line f strings
- Dependencies for csv and os 
- Pseudo code to explain function and purpose 

The code scripts used for this project in the attached Python files titled PyPoll_Election_Outcome_by_Candidate.py and 

## Resources
- Data Source: election_results.csv
- Software: Python 3.7.6, Visual Studio Code 1.58.0

