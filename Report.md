Assignment 5 Report
---------------------

# Team Members


# GitHub link to your (forked) repository

...

# Task 1

Note: Some questions require you to take screenshots. In that case, please join the screenshots and indicate in your answer which image refer to which screenshot.

1. What happens when Raft starts? Why?

Ans: 

2. Perform one request on the leader, wait until the leader is committed by all servers. Pause the simulation.
Then perform a new request on the leader. Take a screenshot, stop the leader and then resume the simulation.
Once, there is a new leader, perform a new request and then resume the previous leader. Once, this new request is committed by all servers, pause the simulation and take a screenshot. Explain what happened?

Ans: 

3. Stop the current leader and two other servers. After a few increase in the Raft term, pause the simulation and take a screenshot. Then resume all servers and restart the simulation. After the leader election, pause the simulation and take a screenshot. Explain what happened.

Ans: 

# Task 2

1. Which server is the leader? Can there be multiple leaders?
Ans: 

2. Perform a Put operation for the key "a" on the leader. Check the status of the different nodes. What changes have occurred and why (if any)?

Ans:

3. Perform an Append operation for the key "a" on the leader. Check the status of the different nodes. What changes have occurred and why (if any)?

Ans: 

4. Perform a Get operation for the key "a" on the leader. Check the status of the different nodes. What changes have occured and why (if any)?

Ans:



# Task 3

1. Shut down the server that acts as a leader. Report the changes in status that you get from the servers that remain active after shutting down the leader.

Ans:

1. Perform a Put operation for the key "a". Then, restart the server from the previous point, and indicate the changes in status for the three servers. Indicate the result of a Get operation for the key "a" to the previous leader.

Ans:

3. Has the Put operation been replicated? Indicate which steps lead to a new election and which ones do not. Justify your answer using the statuses returned by the servers.

Ans:

4. Shut down two servers: first shut down a server that is not the leader, then shut down the leader. Report the changes in status of the remaining servers and explain what happened.

Ans:

5. Can you perform Get, Put, or Append operations in this system state? Justify your answer.

Ans:

6. Restart the servers and note down the changes in status. Describe what happened.

Ans:

## Network Partition

Instantiate the servers so that the leader runs on the first computer. Then, create a network partition. Indicate the changes that occur in the status of a server on the first computer and a server on the second computer and why. Reconnect the computers and explain what happens.

Ans:

Restart the system and instantiate the servers so that the leader runs on the second computer. Then, create a network partition. Indicate the changes that occur in the status of a server on the first computer and a server on the second computer and why. Reconnect the computers and explain what happens.

Ans: 


# Task 4

1. What is a consensus algorithm? What are they used for in the context of replicated state machines? 

Ans: 

2. What are the main features of the Raft algorithm? How does Raft enable fault tolerance? 

Ans: 

3. What are Byzantine failures? How can Raft handle them — and if not, why not? 

Ans: 
