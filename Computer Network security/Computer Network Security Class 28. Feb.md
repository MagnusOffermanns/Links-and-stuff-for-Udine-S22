Book Cryptography and network network security by William Stallings

---
# Chapter 1 Information and network security concepts

```r
== Data Confidentiality ==
	The information is not available to people who should not see it
```

```r
== Privacy ==
The people owing the data can control which information is saved and collected about them 
```

Integrity
```r
== Data Integrity == 
Makes sure that the data is not changed by unothurized people. The data is what it is supposed to be: Sender and Receiver are who they are.
```

```r
== System Integrity ==
The system does what it should do. 
Example: Mail is disappearing
```


```ad-note
title: Availability
The system is available at all times (or when it should be online)
```

```ad-note
title: Authenticity
The members of a system are who they say they are
```

```ad-note
title: Accountability
One can trace who did what, who contributed where the messages came from. Also after a hack or if there is a dispute. Example: github
```

### Why is computer security so difficult and has a lot of challenges
- security is not simple
- many different attacks have to be anticipated
- The  systems need to be updated regularly
- The procedures are sometimes cumbersome for outsiders
- Big choice: which security mechanism to use?
- Little benefit from security till the first security error occurs
- Security is often considered as a impediment to efficient and user-friendly operation. 
- Security is often a second thought after the implementation.


## OSI Security Architecture
```ad-note
title: Security Attack
Action to compromise the information inside a system 
```

```ad-note
title: Security Mechanism
A process that is usd to detect, prevent or recover from a Security attack
```

```ad-note
title: Security service
- A sevice that makes data processing or data transfers more secure
- A service that counters security attacks, they might make use of one or more Security Mechanisms
```

```ad-note
title: Threat
A possiblity for a violation of security. If there are the right circumstance the threat might turn into a attack. A threat is a possible danger that might exploit a vulnearability
```

```ad-note
title: Attack
An active try to break system security and is the next step from a threat.
```