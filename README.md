# election_analysis

# Overview of Election Audit

### Purpose of the election analysis is well defined

We helped Seth and Tom with their initial request for election data. They have asked for additional data:

- The voter turnout per county
- percentage of votes for each county, based on total vote count
- county with the highest turnout

# Election Audit Results

### There is a bulleted list where each election outcome is addressed

![Here are the election results!](https://github.com/jmalauss/election_analysis/blob/main/election_results_snip.png)

1. How many votes were cast in this congressional election?
    - There were 369,711 total votes case in this election.

![total votes](https://github.com/jmalauss/election_analysis/blob/main/total_votes_cast.png)

2. Provide a breakdown of the number of votes and the percentage of total votes for each county in the precinct.
    - **Jefferson** county had a turnout of 38,855 votes, resulting in 10.5% of the total votes cast.
    - **Denver** county had a turnout of 306,055 votes, resulting in 82.8% of the total votes cast.
    - **Arapahoe** county had a turnout of 24,801 votes, resulting in 6.7% of the total votes cast.

![county breakdown](https://github.com/jmalauss/election_analysis/blob/main/county_votes_breakdown.png)

3. Which county had the largest number of votes?
    - **Denver** county had the largest number of votes (306,055 out of 369,711)

![largest turnout](https://github.com/jmalauss/election_analysis/blob/main/largest_turnout_county.png)

4. Provide a breakdown of the number of votes and the percentage of the total votes each candidate received.
    - **Charles Casper Stockham** received 85,213 total votes, resulting in 23.0% of the total votes cast.
    - **Diana DeGette** received 272,892 total votes, resulting in 73.8% of the total votes cast.
    - **Raymon Anthony Doane** received 11,606 total votes, resulting in 3.1% of the total votes cast.

![candidate breakdown](https://github.com/jmalauss/election_analysis/blob/main/candidates_breakdown.png)

5. Which candidate won the election, what was their vote count, and what was their percentage of the total votes?
    - **Diana Degette** won the election with a total of 272,892 total votes, which was 73.8% of the total votes cast. 

![winner!](https://github.com/jmalauss/election_analysis/blob/main/winner.png)

# Election-Audit Summary

there is a statement to the election commission that explores how this script can be used for any election, with two exmaples for modifying the script.

### Starter Code

```
# -*- coding: UTF-8 -*-
"""PyPoll Homework Challenge Solution."""

# Add our dependencies.
import csv
import os

# Add a variable to load a file from a path.
file_to_load = os.path.join("..", "Resources", "election_results.csv")
# Add a variable to save the file to a path.
file_to_save = os.path.join("analysis", "election_analysis.txt")

# Initialize a total vote counter.
total_votes = 0

# Candidate Options and candidate votes.
candidate_options = []
candidate_votes = {}

# 1: Create a county list and county votes dictionary.
county_list = []
county_dict = {}


# Track the winning candidate, vote count and percentage
winning_candidate = ""
winning_count = 0
winning_percentage = 0

# 2: Track the largest county and county voter turnout.
largest_turnout = ""
winning_county = 0


# Read the csv and convert it into a list of dictionaries
with open(file_to_load) as election_data:
    reader = csv.reader(election_data)

    # Read the header
    header = next(reader)

    # For each row in the CSV file.
    for row in reader:

        # Add to the total vote count
        total_votes = total_votes + 1

        # Get the candidate name from each row.
        candidate_name = row[2]

        # 3: Extract the county name from each row.

        # print(county_list[county])        

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
        
        # if county not in county_list:

            # 4b: Add the existing county to the list of counties.

            # county_list.append(county)

            # 4c: Begin tracking the county's vote count.

            # votes per county[county name] = 0

        # 5: Add a vote to that county's vote count.

        # votes per county[county_name] += 1

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
    # for county in county_list:

        # 6b: Retrieve the county vote count.

        # print()

        # 6c: Calculate the percentage of votes for the county.

        # county vote percentage = float(votes) / float(total_votes) * 100

         # 6d: Print the county results to the terminal.

         # print(county)

         # 6e: Save the county votes to a text file.

            # txt_file.write(candidate_results)

         # 6f: Write an if statement to determine the winning county and get its vote count.

# if votes per county is > winning count and 

 # if (votes > winning_count) and (vote_percentage > winning_percentage):
           # winning_count = votes
           # winning_candidate = candidate_name
           # winning_percentage = vote_percentage

    # 7: Print the county with the largest turnout to the terminal.


    # 8: Save the county with the largest turnout to a text file.


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
```

### Final Code

```

# -*- coding: UTF-8 -*-
"""PyPoll Homework Challenge Solution."""

# Add our dependencies.
import csv
import os

# Add a variable to load a file from a path.
file_to_load = os.path.join("..", "Resources", "election_results.csv")
# Add a variable to save the file to a path.

file_to_save = os.path.join("analysis", "election_analysis.txt")

# Initialize a total vote counter.
total_votes = 0

# Candidate Options and candidate votes.
candidate_options = []
candidate_votes = {}

# 1: Create a county list and county votes dictionary.

county_list = []
county_votes_dict = {}

# Track the winning candidate, vote count and percentage
winning_candidate = ""
winning_count = 0
winning_percentage = 0

# 2: Track the largest county and county voter turnout.

largest_turnout_name = ""
largest_turnout_votes = 0

# Read the csv and convert it into a list of dictionaries
with open(file_to_load) as election_data:
    reader = csv.reader(election_data)

    # Read the header
    header = next(reader)

    # For each row in the CSV file.
    for row in reader:

        # Add to the total vote count
        total_votes = total_votes + 1

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

            county_votes_dict[county_name] = 0

        # 5: Add a vote to that county's vote count.

        county_votes_dict[county_name] += 1

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

    for county_name, county_votes in county_votes_dict.items():

        # 6b: Retrieve the county vote count.

        county_votes = county_votes_dict.get(county_name)

        # 6c: Calculate the percentage of votes for the county.

        county_vote_percentage = float(county_votes) / float(total_votes) * 100
        
         # 6d: Print the county results to the terminal.  
        county_results = (
            f'{county_name}: {county_vote_percentage:.1f}% ({county_votes:,})\n')

        print(county_results)

         # 6e: Save the county votes to a text file.

        txt_file.write(county_results)

         # 6f: Write an if statement to determine the winning county and get its vote count.

        if (county_votes > largest_turnout_votes) and (county_vote_percentage > winning_percentage):
            largest_turnout_name = county_name
            largest_turnout_votes = county_votes

    # 7: Print the county with the largest turnout to the terminal.

    winning_county_summary = (
        f'--------------------------\n'
        f'Largest County Turnout: {largest_turnout_name}\n'
        f'--------------------------\n')


    print(winning_county_summary)

    # 8: Save the county with the largest turnout to a text file.

    txt_file.write(winning_county_summary)

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
    
    ```
