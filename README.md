#Report AIT Lab 4 - Virtualization
## CIANI Antony – HERNANDEZ Thomas

![Architecture](assets/reportimg/dockerlogo.png)


##1.	Introduction
In the context of the IT administration course taught by Professor Marcel Graf, this lab goal is to practice the theoretical notions on load balancing learned in the course and better understand them. The provided Docker architecture consists of two simple web application servers, S1 and S2, and a HaProxy load balancer. The manipulations consist in modifying the load balancer configuration and to analyze its behavior with JMeter.

 
 
 
##2. Objectives
•	Deploy a web application in a two-tier architecture for scalability
•	Configure a load balancer
•	Performance-test a load-balanced web application
 

##3. Task 0

1.	[M1] Do you think we can use the current solution for a production environment? What are the main problems when deploying it in a production environment?

2.	[M2] Describe what you need to do to add new webapp container to the infrastructure. Give the exact steps of what you have to do without modifiying the way the things are done. Hint: You probably have to modify some configuration and script files in a Docker image.


3.	[M3] Based on your previous answers, you have detected some issues in the current solution. Now propose a better approach at a high level.


4.	[M4] You probably noticed that the list of web application nodes is hardcoded in the load balancer configuration. How can we manage the web app nodes in a more dynamic fashion?


5.	[M5] In the physical or virtual machines of a typical infrastructure we tend to have not only one main process (like the web server or the load balancer) running, but a few additional processes on the side to perform management tasks. 
For example to monitor the distributed system as a whole it is common to collect in one centralized place all the logs produced by the different machines. Therefore we need a process running on each machine that will forward the logs to the central place. (We could also imagine a central tool that reaches out to each machine to gather the logs. That's a push vs. pull problem.) It is quite common to see a push mechanism used for this kind of task.
Do you think our current solution is able to run additional management processes beside the main web server / load balancer process in a container? If no, what is missing / required to reach the goal? If yes, how to proceed to run for example a log forwarding process?

6.	[M6] In our current solution, although the load balancer configuration is changing dynamically, it doesn't follow dynamically the configuration of our distributed system when web servers are added or removed. If we take a closer look at the run.sh script, we see two calls to sed which will replace two lines in the haproxy.cfg configuration file just before we start haproxy. You clearly see that the configuration file has two lines and the script will replace these two lines.

What happens if we add more web server nodes? Do you think it is really dynamic? It's far away from being a dynamic configuration. Can you propose a solution to solve this?

##4.Task 1 

1. Take a screenshot of the stats page of HAProxy at http://192.168.42.42:1936. You should see your backend nodes. It should be really similar to the screenshot of the previous task.


![Capture](assets/reportimg/captures/Task1_1.PNG)


2. Describe your difficulties for this task and your understanding of what is happening during this task. Explain in your own words why are we installing a process supervisor. Do not hesitate to do more research and to find more articles on that topic to illustrate the problem.

##5.Task 2

1. Provide the docker log output for each of the containers: ha, s1 and s2. You need to create a folder logs in your repository to store the files separately from the lab report. For each lab task create a folder and name it using the task number. No need to create a folder when there are no logs.

Example:
	
	|-- root folder
	 |-- logs
	   |-- task 1
	   |-- task 3
	   |-- ...

2. Give the answer to the question about the existing problem with the current solution.

3. Give an explanation on how Serf is working. Read the official website to get more details about the GOSSIP protocol used in Serf. Try to find other solutions that can be used to solve similar situations where we need some auto-discovery mechanism.

##6.Task 3


##7.Task 4
##8.Task 5

##9.Conclusion
We successfully fulfilled all the required tasks. This lab allowed us to better understand the mechanisms behind a load balancer as well as the pros and cons of the different possible configurations it can offer. 
