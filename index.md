---
title: "2015-04-02 - The Low MQ Story"
author: "Cui Lab"
highlighter: highlight.js
output: pdf_document
job: null
knit: slidify::knit2slides
mode: selfcontained
hitheme: tomorrow
subtitle: null
framework: io2012
widgets: []
---

## GiaB chr18-chr22

- Isolated 1Mbp regions in the 10 samples
- Removed regions with low (< 4000000 reads) or high (> 6500000 reads) coverage
- Among the remaining 258/304 regions, read mapping quality sum to read counts ratio determined
- Considered (10,15,20,25,50) lowest quality regions to corresponding highest quality regions
- Compared how many times each SNP caller ranked highest in HM(Sens,PPV)

---

## GiaB HM Low qual regions

Lowest 10

- MultiGeMS (6), SAMtools (2), VarScan (2)

Lowest 15

- MultiGeMS (9), SAMtools (3), VarScan (3)

Lowest 20

- MultiGeMS (10), SAMtools (6), VarScan (4)

Lowest 25 

- MultiGeMS (14), SAMtools (7), VarScan (4)

Lowest 50

- MultiGeMS (16), SAMtools (22), VarScan (12)

---

## GiaB HM High qual regions

Highest 10

- SAMtools (10)

Highest 15

- SAMtools (15)

Highest 20

- SAMtools (19), VarScan (1)

Highest 25 

- SAMtools (24), VarScan (1)

Highest 50

- SAMtools (46), VarScan (4)

---

## 2015-03-18 Meeting with Prof. Cui

Recall the original objectives

1. Check EM algorithm output on site MultiGeMS "should" have called
2. Analyze true SNP sites quantiles (seperated by quality scores)
3. Meta-analysis of 1Mbp quality regions of varying mapping quality
4. Start using Wei's implementation of MultiGeMS (to-do)

From the results, add to these objectives

3. Prof. Cui agrees that these results should be in the paper, but would also like the results from the UPennMed dataset (in which we might fix the positives and not use PPV).

---

## GiaB 20 MQ SC HM

82.13 90.46 92.46

| Software | FreeBayes | GATK    | SAMtools | MultiGeMS | VarScan |
| -------- | ------- | ------- | ------- | ------- | ------- |
| Region 1 | 0.34821 | 0.18329 | 0.48582 | 0.44252 | 0.44371 |
| Region 2 | 0.7564 | 0.49341 | 0.8509 | <font color="red">0.85136</font> | 0.83011 |
| Region 3 | 0.97795 | 0.94855 | 0.98236 | 0.97623 | 0.97935 |
| Region 4 | 0.99034 | 0.98657 | 0.99169 | 0.98867 | 0.98982 |

---

## GiaB 21 MQ SW TPR

71.78 90.32 91.66

| Software | FreeBayes | GATK    | SAMtools | MultiGeMS | VarScan |
| -------- | ------- | ------- | ------- | ------- | ------- |
| Region 1 | 0.76019 | 0.66037 | 0.8293 | <font color="red">0.84347</font> | 0.79268 |
| Region 2 | 0.90647 | 0.77961 | 0.95246 | 0.6378 | 0.93 |
| Region 3 | 0.96554 | 0.93626 | 0.96845 | 0.92056 | 0.97832 |
| Region 4 | 0.98406 | 0.96864 | 0.97347 | 0.96737 | 0.98205 |

---

## GiaB 22 MQ SW TPR

71.345 89.69 91.345

| Software | FreeBayes | GATK    | SAMtools | MultiGeMS | VarScan |
| -------- | ------- | ------- | ------- | ------- | ------- |
| Region 1 | 0.76976 | 0.68707 | 0.79169 | <font color="red">0.8095</font> | 0.74418 |
| Region 2 | 0.9096 | 0.89599 | 0.95408 | 0.85569 | 0.94627 |
| Region 3 | 0.96895 | 0.96882 | 0.97899 | 0.95396 | 0.981 |
| Region 4 | 0.98506 | 0.97493 | 0.97711 | 0.97239 | 0.98454 |

---

## GiaB 22 MQ SW HM

68.915 84.83 88.915

| Software | FreeBayes | GATK    | SAMtools | MultiGeMS | VarScan |
| -------- | ------- | ------- | ------- | ------- | ------- |
| Region 1 | 0.42985 | 0.32536 | 0.46759 | <font color="red">0.50831</font> | 0.46694 |
| Region 2 | 0.4304 | 0.22919 | 0.60155 | 0.5781 | 0.5821 |
| Region 3 | 0.79038 | 0.53492 | 0.87326 | 0.84394 | 0.86132 |
| Region 4 | 0.96578 | 0.93274 | 0.97112 | 0.96783 | 0.97005 |

---

## GiaB MQ SW HM

69.46 85.92 89.46

| Software | FreeBayes | GATK    | SAMtools | MultiGeMS | VarScan |
| -------- | ------- | ------- | ------- | ------- | ------- |
| Region 1 | 0.4362 | 0.29069 | 0.48735 | <font color="red">0.49534</font> | 0.48233 |
| Region 2 | 0.46265 | 0.2447 | 0.62348 | 0.5602 | 0.59205 |
| Region 3 | 0.83107 | 0.60107 | 0.88526 | 0.86229 | 0.87573 |
| Region 4 | 0.97628 | 0.94943 | 0.98029 | 0.97566 | 0.97824 |

---

## UPennMed chr19-chr22

- Isolated 1Mbp regions in the 34 samples
- Removed regions with low (< 5500000 reads) or high (> 12500000 reads) coverage
- Among the remaining 187/225 regions, read mapping quality sum to read counts ratio determined
- Considered (5,10,15,20,25,50) lowest quality regions to corresponding highest quality regions
- Initially, compared how many times each SNP caller ranked highest in HM(Sens,PPV)

---

##  UPennMed HM

Upon closer examination, there is only nice advantage when looking at the 5 regions lowest in MQ

Lowest 5

- MultiGeMS (4), *No SNP Tie* (1)

Highest 5

- FreeBayes (5)

---

##  Mu value comparison
  
In the regions of low mapping quality, where MultiGeMS ranks well, how do the mu values compare between sites that only MultiGeMS calls, compared to sites where MultiGeMS does not call, but other SNP callers do?
  
GiaB dataset, chrom 22, mq < 71.345, 1762 sites: those called by all SNP callers (1685), in addition to those called exclusively by MultiGeMS (77)

Only result of interest: wilcox.test(snpmu0,notsnpmu0) p-value < 2.2e-16

That is, the mu0 (first mu parameter) values from the set of "true" SNPs are significantly different from those of the "false" SNPs (see email Re: The dataset Wed, 25 Mar 2015 10:26:52).

Additionally, it was often seen that mu0 and mu1 differed significantly.

---

## 2015-03-25 Meeting with Prof. Cui

**Current priorities**

1. Get started on running the entire GiaB dataset (with an extra 1TB of storage for 2-4 weeks) and use the whole-genome results in the paper
2. Design and run a simulation which will support the findings of the real data analysis (which is that MultiGeMS does well in low MQ data)
3. Since the unique aspect of MultiGeMS is the mu variable, select a site where the estimation of mu is advantageous: MultiGeMS makes a correct call when mu is estimated, yet an incorrect call, with results like all the other SNP callers, when not (setting mu = 0)

**Done**

- All the tested SNP callers are fairly up-to-date, the oldest release being SAMtools 0.1.19 which is about 2 years old 

---

## Test Wei's MultiGeMS code

**GiaB chr22 results, with step size 0.1: different from results from Xiaoquan's code**

```R
length(xssnps) # 71514
length(wcsnps) # 67909, already nearly a 4,000 SNP count difference
length(setdiff(xssnps,wcsnps)) # 4039
length(setdiff(wcsnps,xssnps)) #  434
# sites in the intersection of the XS and WC SNP results
intersectsites <- sort(unique(intersect(xssnps,wcsnps))) 
length(intersectsites) # 67475

# Percent of identical lFDR values at the sites of intersection sites, 
# when rounding to 4, 3, 2 and 1 values
length(which(round4df[,2] == round4df[,3]))/length(intersectsites) # 0.823979
length(which(round3df[,2] == round3df[,3]))/length(intersectsites) # 0.906973
length(which(round2df[,2] == round2df[,3]))/length(intersectsites) # 0.957303
length(which(round1df[,2] == round1df[,3]))/length(intersectsites) # 0.989611
```

---

## GiaB: MQ and Coverage per Chr

Questionable QualiMap results

| Chr | Cov Mean | Cov SD | MQ Mean | 
| --- | -------- | ------ | ------- | 
| 18  | 12.64    | 114.22 | 1.51    | 
| 19  |  8.96    | 187.10 | 1.22    | 
| 20  |  9.97    |  73.92 | 1.24    | 
| 21  |  6.38    |  91.09 | 0.80    | 
| 22  |  5.50    |  53.20 | 0.80    | 

---

## Test Wei's MultiGeMS code, part 2

**GiaB chr22 results, with step size 0.01: very similar to results from Xiaoquan's code**

| Chr | XS     | WC     | Intersection | 
| --- | ------ | ------ | ------------ | 
| 18  | 146577 | 146561 | 146515       | 
| 19  | 120849 | 120855 | 120838       | 
| 20  | 112471 | 112470 | 112388       | 
| 21  |  92042 |  92057 |  91713       | 
| 22  |  71517 |  71514 |  71511       | 

---

## Recall GiaB HM results

Chr18

|           | SNP Count | Sens   | PPV    | F HM   |
| --------- | --------- | ------ | ------ | ------ |
| SAMtools  |   141846  | 0.9898 | 0.9181 | 0.9526 |
| VarScan   |   140486  | 0.9791 | 0.9170 | 0.9470 |
| MultiGeMS |   146577  | 0.9897 | 0.8884 | 0.9363 |
| FreeBayes |   146203  | 0.9750 | 0.8774 | 0.9237 |
| GATK      |   194206  | 0.9968 | 0.6753 | 0.8051 |

Chr22

|           | SNP Count | Sens   |   PPV  | F HM   |
| --------- | --------- | -------| ------ | ------ |
| SAMtools  |    70507  | 0.9793 | 0.8241 | 0.8950 |
| VarScan   |    69568  | 0.9711 | 0.8282 | 0.8940 |
| MultiGeMS |    71517  | 0.9834 | 0.8158 | 0.8918 |
| FreeBayes |    75761  | 0.9633 | 0.7544 | 0.8461 |
| GATK      |   111018  | 0.9920 | 0.5301 | 0.6910 |



