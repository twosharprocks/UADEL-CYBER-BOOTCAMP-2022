## Activity File: Advanced Searches with Piping

- Your OMP manager believes there is one specific user that is being targeted by an adversary.

- You have been tasked with running several advanced searches to determine which user is being targeted.


### Instructions

Load and open the **NEW** Windows logs in your Splunk search, specifically the logs named: `winevent_logs_2.csv`
  - Note: There are several windows logs, make sure you are selecting the correct one for this activity: `winevent_logs_2.csv`

1. Design SPL queries to look at the following activity types:

    - An account was successfully logged on. `EventCode=4624 has 302 events`
    - A user account was changed. `EventCode=4738 has 286 events`
    - System security access was granted to an account. `EventCode=4717 has 284 events`
    - A user account was deleted. `EventCode=4726 has 282 events`
    - A user account was locked out. `EventCode=4740 has 292 events`

2. Out of these results, is there an an Account_Name that has a majority of the activity records? Which activity type is it? `Account_Name=user_d has the majority of the logins, and over 70% of these actions are system modifications`
	
    - **Hint:** Account_Name is different from the User field. In this case, the User field can be ignored.

3. Design an SPL query to present the results to your manager with the following information:

    -  The activity type found in the Step 2.
    -  The primary Account_Name.
    -  Simplify the query results to only show the top 50 rows sorted by ComputerName.
    `source="winevent_logs_2.csv" Account_Name=user_d action=modified | sort=ComputerName | head 50`
  
4. Provide a written summary to your manager about what your findings mean.
`A malicious user ("user_d") escalated priviledges, established new system processes ("example_b.exe), which then changed Domain policies across multiple domains and locked out numerous other users`
---

