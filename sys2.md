*Continuing System Design: Part 2*

- different architectural pieces - load balancers, servers etc
- large system is a collection of parts not a sum
- need to decide where will output of one architecutral piece go etc
- how to determine tradeoff? Consistency vs redundancy etc

**5 Characteristics of Distributed Systems**
---
*Scalability*

- capability to grow and manage increased demand e.g flipkart big billion days - website crashed in the first few seconds 
- scale comes in two parts - number of users, number of transactions
- generally number of users is directly proportional to number of transactions
- whenever you scale, you tradeoff something, e.g network speed slow when you scale across continents
- atomic nature of some processes - a process which cannot be parallelised, cannot be broken down. i.e no parallel processing - sequential needed here
- topological dependence - a depends on b , b depends on c and c depends on d and so on. this serial chain is called topological dependence
- types of scaling - vertical and horizontal
	--vertical - upgrade server
	--horizontal scaling - more servers
- advantages and disadvantages of both
**1**
	- if vs (vertical server) crashes, system fails
	- if one server has lag time, entire system lags
	- in horizontal , the task can be reassigned
	- load balancers = check failure rate, if high, assign to other servers
**2**
	- upper limit to vertical scaling
	- no upper limit to horizontal scaling
**3**
	- designing horizontal is harder 
	- maintaining horizontal is harder - if twenty different servers get damaged, more repair

