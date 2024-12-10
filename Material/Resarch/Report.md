
[TOC]

# Report 

WEEK 1 , DATE 12 TO 15 MAY

## INTRODUCTION TO DGA

An infected machine periodically uses a seed and a domain generation algorithm (DGA) to automatically generate a large batch of domain names, and does a Domain Name Service (DNS) query to discover the domains’ IP addresses.

The command-and-control server contacts an infected machine by registering and using one of the generated domain names. If this domain is blacklisted, it can move to another of the generated domains. 

If a machine can be detected querying malware DGA domains, it may be possible to disinfect or quarantine it before the infection produces any symptoms.

## APPROACHES

- Use machine learning to build a classifier based on features of DGA domain names.
- DGAs can be determined from captured malware code, or by capturing the DNS traffic of a machine infected with malware that uses a new DGA.
- Look for **clusters of similar domains being queried by multiple clients**. This only ==catches infections in their later stages, when they have spread to several clients==. ==Combine this with other approaches, so that if a DGA is not detected early it may be detected later on.==



## SCENERIOS FOR

### INFECTION

| STAGE   | KEY POINT                                                   | NO. OF HOST INFECTED                          |
| ------- | ----------------------------------------------------------- | --------------------------------------------- |
| INITIAL | Each host must be individually checked.                     | LESS                                          |
| FINAL   | Pattern in overall network traffic visible after clustering | MULTITUDE OF BOTS TRYING TO CONNECT WITH C&C. |

### DGA

| DISCOVERED | BLACKLISTED | KEY POINT                       |
| ---------- | ----------- | ------------------------------- |
| YES        | YES         | Wont generate NxDomain traffic. |
| YES        | NO          | Lot of NxDomain                 |
| NO         | NO          | Lot of NxDomain                 |



## IDEA 

- Look for anomalies in outgoing DNS queries.

- ==Most of the DGA-generated (random) domains that a bot queries would result in Non-Existent Domain (NXDomain) responses, and that bots from the same botnet (with the same DGA algorithm) would generate similar NXDomain traffic==.

## OPEN QUESTIONS

- What features to see in the domains 
- Classifier to use 
  - Deep Learning approach or 
  - Standard ML (SVM, Naive Bayes .. etc)
- Distance matrix to use for clustering 
- Clustering Method (K-Mean,X-Mean, Hiearichal, ...) 
- Cleaning the data (Pre Processing)
- What can we learn from benign domain
- Identify blacklisted domains.

## DESIGN CHOICES

### WHEN MONITORING EVERY SINGLE HOST 

1. A Filter to raise flags for anomolus domains  

2. Then check if they are anomolus but benign 
3. If bad further process them by same classifier. 
4. Figuring it out.



### WHEN MONITORING WHOLE NETWORK

Use a combination of clustering and classification algorithms. 

1. The clustering algorithm clusters domains based on the similarity in the make-ups of domain names as well as the groups of machines that queried these domains. 
2. The classification algorithm is used to assign the generated clusters to mod- els of known DGAs. 
3. If a cluster cannot be assigned to a known model, then a new model is produced, indicating a new DGA variant or family.

## SUMMARY OF DESIGN

![Screenshot 2020-05-15 at 7.10.16 PM](/Users/vikramadityasingh/Desktop/Screenshot 2020-05-15 at 7.10.16 PM.png)



![Screenshot 2020-05-15 at 7.18.18 PM](/Users/vikramadityasingh/Library/Application Support/typora-user-images/Screenshot 2020-05-15 at 7.18.18 PM.png)



## REFERENCES

A Taxonomy of Domain-Generation Algorithms

CLEAN: an Approach for Detecting Benign Domain Names based on Passive DNS Traffic

Finding Domain-Generation Algorithms by Looking at Length Distributions

From Throw-Away Traffic to Bots: Detecting the Rise of DGA-Based Malware

