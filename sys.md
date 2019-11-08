 - Atleast one sys design round
 - Not much expected from students
 - Ask Clarifications, test whiteboarding
 - Design questions - no standard answer like cp 
 

**Steps**

* requirement clarification *
	- want you to think for the constraints, clarifications etc
	- ask questions about scope of problem
	- There is an entire cycle when you give one 
		MVP *(Minimum Viable Product)* - minimum product you give to user and ask user to test it, user gives feedback and product improved	- want to know your thinking process rather than a correct answer
	- scope = what exact part/features do you want me to design
	- don't know what they are looking for, 
	you focused on features they needed scaling

**Example**
	**`Twitter`**
	- Requirement Analysis
		- Whom all can we direct message? Can we direct message a celebrity
		- Can you follow people, can they follow you back/
		- Do you have to accept follow requests (pros- saved from trolls,  cons- difficult for celebrities)
		- should we design for timeline? Which tweet should have more priority
		- allow photos and videos - load on server increased but more user friendly
		- hangouts vs messanger - fast vs more features
		- focus on backend or focus on frontend
		- search tweets - how to search
		- hashtags - how to rank topics, focus on geology, retweets - number or number per second (grows slowly but more / grows fast but lesser)
		- emails for tweet / which tweets need to emailed 
		- how many servers needed for this etc

Suppose you're HR at google. New office is to be opened. A party to be thrown for that. You have to organise this party. How to do that?

- Venue (City/Hotel/How many floors) 
- Number of guests (100-200)
- Budget (1 crore)
- Distance of the venue 
- Timing n Date
- Food Preferences 

Let's say you did not ask clarifications and directly jumped. All of sudden you realise party is in a small city. A lot things are missed out. People not happy. Raw materials not available. A whole set of things can go wrong!!

**Step2 : System Interface Definition**

- Define the APIs needed (APIs are the system calls needed)
- Contract - In an API contract is API definition i.e exact requirement 
- Get the broad requirements in contract form i.e convert requirement to system calls
- e.g posting tweet broad requirement 
	-- contract 
		--- user id needed (handle for1 1 billion users. how do you handle user ids? If by name, then there might be more than one people with same name. How do you handle that?
		--- tweet location (remeber we had hot tweets feature. things important in America may not be important in India 
		--- user location (user in Japan, tweet in India) - something fishy - send a mail to user

		--- timestamp (displaying timeline etc)
- e.g create timeline for users 
	-- user id needed, location, friend list, follow list, timestamp etc
- e.g favorite a tweet - how to decide what tweet is important
	-- give user an option to decide what are his favorites
	-- based on that decide push notification tweets
	-- don't go into much detail in this part
	-- this is why asking scope is important

**Step 3: BackEnd Estimation **

- Always  a good idea to estimate scale
	-- design for 100 people, system booms, 1 billion people now. everything crashes
- Paritioning - Suppose you have a network. someo f packets dropped. network breaks. Goblal system of networks now paritioned into two networks. because connections broken 
- Consistency - input data, all users can read at same time. All read the same data
- Load Balancing - all load cannot be put on one server. Server will crash. Load need to be balanced
- caching - cache something to retrieve it faster
---e.g scale expections - how many tweets, how many users, number of tweet views etc
--- ratio of reading/writing e.g 80/20 --more servers needed for reading
--- how much storage needed - number of users having photos and videos --we will need more servers for that. 
--- network bandwidth - tcp or udp
