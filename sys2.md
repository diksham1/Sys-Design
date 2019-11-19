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


*Relibility*

- probability that a system will fail in a given period in time
- e.g for amazon, if some error occurs, card transaction never fails. We need to maintain redundancy here. 
- need to determine amount of redundancy - this is called replication factor
- replication factor of three means three copies of data is kept. google file system has a replication factor of three. i.e three copies of data is stored

*Availability*

- availability is the time system remains functional to perform it's duties. 
- e.g suppose time period three years. and mu aircraft was available for 99.99% of time. If the aircraft is down for maintainance, it's not considered available at that time. 
- something that is available may not be reliable
- the chances of failure is unreliability
- if reliable, then surely available
- e.g unreliable aircraft, fails frequently but we repair fast and so high availability

*Efficiency*

- low latency - highly efficient
- high throughput - high efficiency
- low number of packets dropped - high efficiency

how do you measure? 10000 messages of text vs 100 messages of video? one is number of messages, other is volume of messages.

is volume better then?

**we'll come to that**

*Manageability*

- suppose the distributed system is small. 
- is it always manageable?
- in an organisation, employees are changing. need to ensure the system is easy to operate and maintain. 
- suppose power outage occurs, systems fail when recovers. so maintainence time should be less. 
- two things involved
- diagnosing the problem - finding root cause
- ease of solving the problem - automation neeeded , humans cannot always monitor, 

- another thing, upto how much level you let the fault occur. no big system failure happens all of a sudden
- let's say you're desiging a monitoring system 
-- working normally initiallly, at some point , request failures started increasing but sill continued working. these signs were warning signs, you ignored it. Report the first symptoms of failure. don't wait till the time system fails. 

---

**Load Balancing**

- Jobs of a load balancer
	-- spreads traffic across a cluster of servers
	--improves avalability and responsiveness
	-- keeps track of health of servers
	-- distributes traffic across healthy servers
	
	let's say three servers with 1GB/s capacity. 900MB/s is coming. is it a fine idea to give it to only one server?
	should I distribute it?

	basically why is load balancing needed?
	
	even if one server can handle the load, too much load will cause heating and may cause parts to fail. this will avoid lag, slowness, overheating.
	more overheating, more costs on cooling the system. generally there are heat sensors, they sense heat and cool according. if heat is less, billions of dollars saved.

*Read about how deepmine helped Google*
 take away load balancing is not always for large data, it also protects temperature sensitive equipments, improving responsiveness

---
*Typical System*	
- Where to keep load balancer - maybe all, maybe some
---
Load Balancing

- What if load balancer fails?
- We maintain cluster of load balancers
- some are active load balancers, some in passive state
- one fails, passive is started, while engineers look on the issue
- load balancers helps you to 
	-- scale - data can be scaled
	-- reliability, scalability
	-- efficiency - parallel tasks
	-- manageability - continuosly checks the status of servers and helps you find which exact parts are failing
		--- provides insights regarding data traffic
	
	mostly detecting the problem is tougher than fixing it.

**Load Balancers are having backend algorithms to do the work for you**

- first step - doing a health check
	-- find which servers are working fine
---
Load Balancing Algorithms
- Least Connection Method - allocate to the server with least clients connected to
- Least Response time - give to the one with least response time
- Least BandWidth method - give to the one which is handling least amount of data volume
- Round Robin method - assign in a round robin method
- weighted Round Robin - Assign on the basis of capacity. first takes 3 requests, second 4, third one and so on. 
- Create Hash of IP - H(IP) will be used to find the server for a data


---
*Caching*

- Caches are generally kept near front end
- Let's say you have a connection to a server. each server will have two components, cache and memory. Cache is faster than server memory which is in turn faster than data base storage and network storage. 


**Cache Invalidation**

Let's say you have a ppt you are editing in computer. Say you make some changes. If it's not reflected back in the database then it's inconsistent. SOlving this problem of incosistency in cache is called cache invalidation. 
  
