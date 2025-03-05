# EVOTING-SYSTEM
1. Introduction
The E-Voting System is a secure, GUI-based desktop application designed to facilitate electronic voting using Python (Tkinter) for the user interface and PostgreSQL as the backend database. This system ensures a transparent and tamper-proof voting process by implementing user authentication, candidate management, and real-time vote counting. An e-voting system is a digital platform that allows users to cast their votes electronically. This system ensures secure, efficient, and transparent voting processes. In this project, we will build a desktop-based e-voting system using:

Tkinter: For the graphical user interface (GUI).

PostgreSQL: For storing user data, candidate information, and votes.

Email Integration: To send confirmation emails to users after voting and to send results to administrators.

2. System Architecture
The system is divided into the following components:

Frontend (Tkinter GUI):

Registration Page

Login Page

Voting Page

Results Page

Backend (PostgreSQL Database):

Stores user credentials, candidate details, and vote records.

Email Integration:

Sends confirmation emails to users after voting.

Sends election results to administrators.

3. Database Design
The database is the backbone of the system. It consists of the following tables:

3.1 Users Table
Stores user information, including whether they have voted.

Column Name	Data Type	       Description
id	        SERIAL	         Primary key (auto-incrementing)
username	  VARCHAR(50)	     Unique username for login
password	  VARCHAR(50)	     User password (plaintext)
email	      VARCHAR(100)	   User email address
voted	      BOOLEAN	         Whether the user has voted

3.2 Candidates Table
Stores candidate information and their vote counts.

Column Name	Data Type	     Description
id	        SERIAL	       Primary key (auto-incrementing)
name	      VARCHAR(100)	 Candidate name
votes	      INT	           Number of votes received

3.3 Votes Table
Stores vote records to track which user voted for which candidate.

Column Name	  Data Type	    Description
id	          SERIAL	      Primary key (auto-incrementing)
user_id	      INT	          Foreign key referencing users
candidate_id	INT	          Foreign key referencing candidates

4. System Workflow
The system follows a step-by-step workflow:

4.1 Registration
Users register by providing a username, password, and email.

The system checks for duplicate usernames and emails.

If valid, the user is added to the users table.

4.2 Login
Users log in using their username and password.

The system verifies the credentials against the users table.

If valid, the user is redirected to the voting page.

4.3 Voting
Users see a list of candidates on the voting page.

They select a candidate and cast their vote.

The system updates the candidates table (vote count) and the votes table (vote record).

The user's voted status in the users table is set to TRUE.

4.4 Confirmation Email
After voting, the system sends a confirmation email to the user's registered email address.

The email contains a thank-you message and confirms that their vote has been recorded.

4.5 Results
The system calculates the total votes for each candidate from the candidates table.

The results are displayed on the results page.

Administrators can also receive the results via email.

5. Email Integration
Email functionality is implemented using Python's smtplib library. The system sends two types of emails:

Confirmation Email:

Sent to the user after they vote.

Contains a thank-you message.

Results Email:

Sent to administrators after the election ends.

Contains the final vote counts for all candidates.


6. Conclusion
This e-voting system provides a basic yet functional framework for conducting electronic voting. By integrating Tkinter for the GUI, PostgreSQL for the database, and email for notifications, the system ensures a seamless user experience. While this implementation is suitable for small-scale elections, further enhancements are required for large-scale, real-world applications.

