# Reports

[TOC]

## Report I - Dissecting Domain Generation Algorithms Eight Real World DGA Variants - 2016 

### Core Activities

#### ESTABLISHING COMMAND & CONTROL 

Essential component is establishing command & control (C&C) communication between the attacker and hacked network. 

#### A COMMON C&C METHOD

Adversaries have stopped using hard-coded domain lists and IP addresses, which are useless once blocked.

> DGAs have quickly become the main method attackers use to remotely communicate.

 A DGA typically has three components:

- A time-sensitive “seed”
- A domain “body” generator that uses this seed
- A  set of top-level domains (TLDs) 

The domain body generator is the main part of a DGA, and can basically be anything―a random string of characters, concatenation of random words, a constant part followed by a changing sufix.

The set of TLDs, however, must contain real-world values that determine under which Web entities the generated domains are registered. 

#### TRADITIONAL METHODS FAIL TO DETECT AND BLOCK DGAS 

Even when a certain DGA is known (for example, by reverse engineering a malware sample), it’s still dificult―or even impossible―to effectively block it.

- There is the sheer number of possible domains that can be generated. 

- The seed can be the real issue, basically any value that can be reliably obtained via the Internet by both the malware and its operator. 

  > Predicting these values in advance is of course impossible, and most iltering solutions do not support dynamic generation of domains to block. 

- 

To detect randomly-generated domains by their patterns, without knowing the algorithm in advance

- There is a strong chance for false positives, as many legitimate websites use load-balancing servers and other strange looking domain names, and the tiny ratio of DGA trafic compared to regular trafic makes false positives almost a certainty.
- DGA body generators can take many forms and aren’t necessarily a long string of random characters

## 