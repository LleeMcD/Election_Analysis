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

## Resources
- Data Source: election_results.csv
- Software: Python 3.7.6, Visual Studio Code 1.58.0

#### Apendix A
###### Python Code for Candidate Results
# Add our dependencies.
import csv
import os
 # Assign a variable to load a file from a path.
file_to_load = os.path.join("Resources", "election_results.csv")
# Assign a variable to save the file to a path.
file_to_save = os.path.join("analysis", "election_analysis.txt")
# Initialize a total vote counter.
total_votes = 0
# Candidate options and candidate votes.
candidate_options = []
candidate_votes = {}
# Track the winning candidate, vote count, and percentage.
winning_candidate = ""
winning_count = 0
winning_percentage = 0
# Open the election results and read the file.
with open(file_to_load) as election_data:
    file_reader = csv.reader(election_data)
    # Read the header row.
    headers = next(file_reader)
    # Print each row in the CSV file.
    for row in file_reader:
        # Add to the total vote count.
        total_votes += 1
        # Get the candidate name from each row.
        candidate_name = row[2]
        # If the candidate does not match any existing candidate, add the
        # the candidate list.
        if candidate_name not in candidate_options:
            # Add the candidate name to the candidate list.
            candidate_options.append(candidate_name)
            # And begin tracking that candidate's voter count.
            candidate_votes[candidate_name] = 0
        # Add a vote to that candidate's count.
        candidate_votes[candidate_name] += 1

# Save the results to our text file.
with open(file_to_save, "w") as txt_file:
    # After opening the file print the final vote count to the terminal.
    election_results = (
        f"\nElection Results\n"
        f"-------------------------\n"
        f"Total Votes: {total_votes:,}\n"
        f"-------------------------\n")
    print(election_results, end="")
    # After printing the final vote count to the terminal save the final vote count to the text file.
    txt_file.write(election_results)
    for candidate_name in candidate_votes:
        # Retrieve vote count and percentage.
        votes = candidate_votes[candidate_name]
        vote_percentage = float(votes) / float(total_votes) * 100
        candidate_results = (f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")
        # Print each candidate's voter count and percentage to the terminal.
        print(candidate_results)
        #  Save the candidate results to our text file.
        txt_file.write(candidate_results)
        # Determine winning vote count, winning percentage, and winning candidate.
        if (votes > winning_count) and (vote_percentage > winning_percentage):
            winning_count = votes
            winning_candidate = candidate_name
            winning_percentage = vote_percentage
    # Print the winning candidate's results to the terminal.
    winning_candidate_summary = (
        f"-------------------------\n"
        f"Winner: {winning_candidate}\n"
        f"Winning Vote Count: {winning_count:,}\n"
        f"Winning Percentage: {winning_percentage:.1f}%\n"
        f"-------------------------\n")
    print(winning_candidate_summary)
    # Save the winning candidate's results to the text file.
    txt_file.write(winning_candidate_summary)


###### Python Code for Candidate and County Results
# Add our dependencies.
import csv
import os

# Add a variable to load a file from a path.
file_to_load = os.path.join("Resources", "election_results.csv")
# Add a variable to save the file to a path.
file_to_save = os.path.join("analysis", "election_analysis.txt")

# Initialize a total vote counters.
total_votes = 0
total_county_votes = 0

# Candidate Options and candidate votes.
candidate_options = []
candidate_votes = {}

# 1: Create a county list and county votes dictionary.
county_list = []
county_votes = {}

# Track the winning candidate, vote count and percentage
winning_candidate = ""
winning_count = 0
winning_percentage = 0

# 2: Track the largest county and county voter turnout.
largest_turnout = ""
most_county_votes = 0
county_vote_percentage = 0

# Read the csv and convert it into a list of dictionaries
with open(file_to_load) as election_data:
    file_reader = csv.reader(election_data)

    # Read the header row
    headers = next(file_reader)

    # For each row in the CSV file.
    for row in file_reader:
        # Add to the total vote count.
        total_votes += 1
        total_county_votes += 1

        # Get the candidate name from each row.
        candidate_name = row[2]

        # 3: Extract the county name from each row.
        county_name = row[1] 

        # If the candidate does not match any existing candidate add it to
        # the candidate list
        if candidate_name not in candidate_options:

            # Add the candidate name to the candidate list.
            candidate_options.append(candidate_name)

            # And begin tracking that candidate's voter count.
            candidate_votes[candidate_name] = 0

        # Add a vote to that candidate's count
        candidate_votes[candidate_name] += 1

        # 4a: Write an if statement that checks that the
        # county does not match any existing county in the county list.
        if county_name not in county_list:            
            
            # 4b: Add the existing county to the list of counties.
            county_list.append(county_name)

            # 4c: Begin tracking the county's vote count.
            county_votes[county_name] = 0

        # 5: Add a vote to that county's vote count.
        county_votes[county_name] += 1 
       

# Save the results to our text file.
with open(file_to_save, "w") as txt_file:

    # Print the final vote count (to terminal)
    election_results = (
        f"\nElection Results\n"
        f"-------------------------\n"
        f"Total Votes: {total_votes:,}\n"
        f"-------------------------\n\n"
        f"County Votes:\n")
    print(election_results, end="")

    txt_file.write(election_results)

    # 6a: Write a for loop to get the county from the county dictionary.
    for county_name in county_votes:
        # 6b: Retrieve the county vote count.
        county_vote_count = county_votes[county_name]
        # 6c: Calculate the percentage of votes for the county.
        county_voting_percentage = float(county_vote_count) / float(total_votes) *100
        county_results = (f"{county_name}: {county_voting_percentage:.1f}% ({county_vote_count:,})\n")
        # 6d: Print the county results to the terminal.
        print(county_results)
        # 6e: Save the county votes to a text file.
        txt_file.write(county_results)
        # 6f: Write a decision statement that determines the county with the largest vote count 
        if (county_vote_count > most_county_votes) and (county_voting_percentage > county_vote_percentage):
            most_county_votes = county_vote_count
            largest_turnout = county_name
            county_vote_percentage = county_voting_percentage
         
    # 7: Print the county with the largest turnout to the terminal.
    largest_turnout_summary = (     
        
        f"-------------------------\n"
        f"Largest County Turnout: {largest_turnout}\n"       
        f"-------------------------\n")      
    print(largest_turnout_summary)

    # 8: Save the county with the largest turnout to a text file.
    txt_file.write(largest_turnout_summary)

    # Save the final candidate vote count to the text file.
    for candidate_name in candidate_votes:

        # Retrieve vote count and percentage
        votes = candidate_votes.get(candidate_name)
        vote_percentage = float(votes) / float(total_votes) * 100
        candidate_results = (
            f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")

        # Print each candidate's voter count and percentage to the
        # terminal.
        print(candidate_results)
        #  Save the candidate results to our text file.
        txt_file.write(candidate_results)

        # Determine winning vote count, winning percentage, and candidate.
        if (votes > winning_count) and (vote_percentage > winning_percentage):
            winning_count = votes
            winning_candidate = candidate_name
            winning_percentage = vote_percentage

    # Print the winning candidate (to terminal)
    winning_candidate_summary = (
        f"-------------------------\n"
        f"Winner: {winning_candidate}\n"
        f"Winning Vote Count: {winning_count:,}\n"
        f"Winning Percentage: {winning_percentage:.1f}%\n"
        f"-------------------------\n")
    print(winning_candidate_summary)

    # Save the winning candidate's name to the text file
    txt_file.write(winning_candidate_summary)
