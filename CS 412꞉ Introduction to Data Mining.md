---
tags: ['CS 412: Introduction to Data Mining', school]
title: 'CS 412: Introduction to Data Mining'
created: '2020-01-29T17:51:52.498Z'
modified: '2020-01-31T15:53:01.290Z'
---

# CS 412: Introduction to Data Mining
---
## Week 1

Notes:

 - The Apriori Algorithm
https://www.hackerearth.com/blog/developers/beginners-tutorial-apriori-algorithm-data-mining-r-implementation
Apriori algorithm is a classical algorithm in data mining. It is used for mining frequent itemsets and relevant association rules. It is devised to operate on a database containing a lot of transactions, for instance, items brought by customers in a store.

- Mining Frequent Patterns by Exploring Vertical Data Format
- FPGrowth
- Closed Pattern: Lossless compression 
Closet+

- [Support/Confidence](https://www.quora.com/What-is-support-and-confidence-in-data-mining#)

## Week 2

- 3.1. Limitation of the Support-Confidence Framework
  - Not all patterns/rules are interesting 
  - Objective: Support and correlation. 
  - Subjective: Relevant to users request. 
  - Data may give wrong results/correlations. 

- 3.2. Interestingness Measures: Lift and χ2
  - Lift: Measure of dependent/correlated events: A measure of the performance of a targeting model (association rule) at predicting or classifying cases as having an enhanced response (with respect to the population as a whole), measured against a random choice targeting model.
  - χ2: A way to test correlated events


- 3.3. Null Invariance Measures
  - null-invariance: value does not change with the # of null-transactions. 
  - Can be crucial for analysis of massive transactions. Many transactions may contain neither milk nor coffee. 
  - 

