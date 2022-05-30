```pdf
{
"url": "/Artificial intelligence and Cybersecurity/Udine/Advanced Data Systems for big data/slides/0_introduction.pdf", 
"page": 1,
"scale": 1.5,
"fit": false,
"rect": [0,0,270,360]
}
```

```pdf
{
"url": "/Artificial intelligence and Cybersecurity/Udine/Advanced Data Systems for big data/slides/0_introduction.pdf", 
"page": 2,
"scale": 1.5,
"fit": false,
"rect": [0,0,270,360]
}
```

email,contact, webpage, normally last minute information in the news box, on his website link to slides and website of course, there is a ==mailing list== we should write him if we want to get added to the mailing-list. On his website there is a list of all links to all recordings from last year.

==Exam modalities:==
Exam will be a written test. Students can ask for a oral exam in special cases.



```pdf
{
"url": "/Artificial intelligence and Cybersecurity/Udine/Advanced Data Systems for big data/slides/0_introduction.pdf", 
"page": 3,
"scale": 1.5,
"fit": false,
"rect": [0,0,270,360]
}
```

```pdf
{
"url": "/Artificial intelligence and Cybersecurity/Udine/Advanced Data Systems for big data/slides/0_introduction.pdf", 
"page": 4,
"scale": 1.5,
"fit": false,
"rect": [0,0,270,360]
}
```
What are we talking about? We move the way from a designer of a database, design and implementation to how does a [[DBMS]] work from the inside.

What happens when a user sends a query. How do we optimize a query.
We will go on talking about relational databases. How can we make that the query is executed the fastest?

We will look at different join algorithms and their speed.

We look at local databases. All the computation on one machine. Then we will move to Databases that also are distributed. 

How do we design distirbuted databases and how do we optimize databases?

Then we look at transaction managment -> concurency control and relyability

Semistructured Data and XML will be handled in the last part of the lecture with 

```pdf
{
"url": "/Artificial intelligence and Cybersecurity/Udine/Advanced Data Systems for big data/slides/0_introduction.pdf", 
"page": 5,
"scale": 1.5,
"fit": false,
"rect": [0,0,270,360]
}
```

This are the books he uses.
First book for query opitmization

second book for Distributed database systems.

```pdf
{
"url": "/Artificial intelligence and Cybersecurity/Udine/Advanced Data Systems for big data/slides/1a_query_processing_sil_7ed_ch15_SPLIT.pdf", 
"page": 1,
"scale": 0.9,
"fit": false,
"rotation": 90,
"rect": [0,0,550,850]
}
```

```pdf
{
"url": "/Artificial intelligence and Cybersecurity/Udine/Advanced Data Systems for big data/slides/1a_query_processing_sil_7ed_ch15_SPLIT.pdf", 
"page": 2,
"scale": 0.9,
"fit": false,
"rotation": 90,
"rect": [0,0,550,850]
}
```

How do you choose the best algorithm. One needs a metric. In this case we want to minimize time used for the algorithm.

We will first model our cost metric. How do we measure the speed of an algorithm? We will use a different cost model than normally.

Additonally we will measure how we can evaluate a full expression. For example multiple algorithms in a row in a pipeline. 

```pdf
{
"url": "/Artificial intelligence and Cybersecurity/Udine/Advanced Data Systems for big data/slides/1a_query_processing_sil_7ed_ch15_SPLIT.pdf", 
"page": 3,
"scale": 0.9,
"fit": false,
"rotation": 90,
"rect": [0,0,550,850]
}
```

How does a basic querying process work?
- query -> input
- parser and translator:
 check the syntax of the query,  structure for correctness.
 this is then translated into a [[relational algebra]] expression -> many of them as there are multiple [[logical equivalence|logically equivalent]] once.
 
example:
```sql
select surname
from Students
where birthday > 2000
```
lets tranlate this into [[relational algebra]]

$\pi_{surname} \rightarrow \delta_{birthday>2000} \rightarrow \text{Stud}$
$\pi_{surname} \rightarrow \delta_{birthday>2000} \rightarrow \pi{surname,birthday} \rightarrow \text{Stud}$

- optimizer 
Calculates a cost for the individual expressions then chooses the best one.
```pdf
{
"url": "/Artificial intelligence and Cybersecurity/Udine/Advanced Data Systems for big data/slides/1a_query_processing_sil_7ed_ch15_SPLIT.pdf", 
"page": 5,
"scale": 0.9,
"fit": false,
"rotation": 90,
"rect": [0,0,550,850]
}
```

==Why is there a need to translate from sql to [[relational algebra]]?==
Why are there multiple possible expressions for the same query?

[[SQL]] tell you what one wants and is therefore also called a [[declarative language]]
[[relational algebra]] is telling you how to get what we want (operational)

By using a declarative language the burden of complexity is pushed from the user of a database to the designer of the database.

In the end before execution we will translate the[[relational algebra]] to a [[Query execution plan]]. 

The [[Query execution plan|QEP]] has more information than a [[relational algebra]] expression. It also defines the algorithms used to perform the [[relational algebra]] operations.

Additionally there is also a modality of operation i.e. will it be pipelined? We create multiple [[Query execution plan|QEP]] and every one gets a cost value c1,c2,...,cn. We then choose the [[Query execution plan|QEP]] with the lowest cost. We do not have the real cost but we estimate the cost that the [[Query execution plan|QEP]] has.

```pdf
{
"url": "/Artificial intelligence and Cybersecurity/Udine/Advanced Data Systems for big data/slides/1a_query_processing_sil_7ed_ch15_SPLIT.pdf", 
"page": 6,
"scale": 0.9,
"fit": false,
"rotation": 90,
"rect": [0,0,550,850]
}
```

The user is not awaited to know the most efficient algorithms to the calculation

```pdf
{
"url": "/Artificial intelligence and Cybersecurity/Udine/Advanced Data Systems for big data/slides/1a_query_processing_sil_7ed_ch15_SPLIT.pdf", 
"page": 7,
"scale": 0.9,
"fit": false,
"rotation": 90,
"rect": [0,0,550,850]
}
```

How do we decide which [[Query execution plan|QEP]] is best? We have statistical data that decides which one is best.

# Measuring of query cost
```pdf
{
"url": "/Artificial intelligence and Cybersecurity/Udine/Advanced Data Systems for big data/slides/1a_query_processing_sil_7ed_ch15_SPLIT.pdf", 
"page": 12,
"scale": 0.9,
"fit": false,
"rotation": 90,
"rect": [0,0,550,850]
}
```

One could also optimize for memory, we do only optimize for speed.

What are resources that we can use with a database call?

- disk access (i/o operations)
	- number of [[seek]]s
	- number of blocks read
	- number of blocks written
- CPU usage
- network communication

We have two forms of communication
CPU  <-> [[Random access memory|RAM]] and
[[Random access memory]] <-> [[hard-disk]]

as the communication between the CPU and the RAM is so fast we ignore it and only consider the reads and writes between the [[Random access memory|RAM]] and the [[hard-disk]].

New technologies change the game -> SSD make [[hard-disk]]s very fast. Then we need to change our cost model. 

```pdf
{
"url": "/Artificial intelligence and Cybersecurity/Udine/Advanced Data Systems for big data/slides/1a_query_processing_sil_7ed_ch15_SPLIT.pdf", 
"page": 13,
"scale": 0.9,
"fit": false,
"rotation": 90,
"rect": [0,0,550,850]
}
```

$t_s$ and $t_T$ depend on the hardware. Therfore at installation [[DBMS]] do tests to define the values.


