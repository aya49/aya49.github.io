---
title: "Yue, Alice, et al. 'Identifying differential cell populations in flow cytometry data accounting for marker frequency.' BioRxiv (2019): 837765."
name: "Identifying maximal differential cellpopulations in flow cytometry data accounting for dependence between cell populations"
date: 2020-09-30
categories: 
  - publications
excerpt_separator: <!--more-->
---

**Authors**: Alice Yue, Cedric Chauve, Maxwell Libbrecht, Ryan Brinkman

<a href="http://doi.org/10.1101/837765" target="_blank"><input class="button b1" type="button" value="doi" /></a> <a href="https://docs.google.com/presentation/d/1rocCQnFISWXx0JLVCTAxb0YNOcIpmvUq3RPiM_TNoV4/edit?usp=sharing" target="_blank"><input class="button b1" type="button" value="slides" /></a> <a href="https://docs.google.com/presentation/d/1o03ZqVq690-gHAB8AbWMNKWDvMKUYOocEHustEmZMNM/edit?usp=sharing" target="_blank"><input class="button b1" type="button" value="poster" /></a> <a href="https://github.com/aya49/flowGraph" target="_blank"><input class="button b2" type="button" value="code" /></a>

<!--more-->

We propose SpecEnr (specific enrichment), a cell population score that accounts for dependency between cell populations, and a method that harness SpecEnr properties to find candidate biomarkers for disease diagnosis in flow cytometry (FCM) data.

### Preliminaries


A **cell population** is a group of cells that does not/contain the the same set of markers. For example, cell population A+B+C- contans markers A and B but does not contain marker C. Given a set of markers (A, B, C), all possible cell populations can be organized in a cell hierarchy, or a lattice as shown in the figure below. Cell populations are analogous to frequent itemsets e.g. given a set of markers/products (Apples, Banana, Candies), a set of cells/transactions (person 1 buys A and B but not C, person 2 ...), you can enumerate all possible cell populations/itemsets as below.

![cell hierarchy](https://user-images.githubusercontent.com/22086811/95698794-959f3a00-0bf7-11eb-8f4a-9794ff6b17e3.png){:class="img-responsive"}

A FCM **sample** is a vector containing the cell count or the number of cells in each cell population.

A **sample class** is a class label to which a sample belongs to. For example, a set of samples may belong in the control group while another set of samples belong in the experiment group.

### Problem

We want to know which cell populations an experiment drives a change in as these cell population can act as potential biomarkers for disease diagnosis. The easiest way to find these driver cell populations is to perform a statistical significance test on each cell population across the two sample classes. However, using traditional cell population abundance scores, such as cell count and proportion (cell population cell count over total cell count), we may get false positive results. For example, if a disease increases the production of helper T-cells by 900 cells/mcL of blood, then the overall number of T-cells would also increase by the same amount. In other words, cell populations who share cells are dependent on each other. In our example, we only want to flag helper T-cells, but a significance test would also flag T-cells.

### Solution

We propose comparing SpecEnr instead, a cell population score that accounts for such dependency between a cell population and its ancestors. Our workflow shown below.

![workflow](https://user-images.githubusercontent.com/22086811/95698802-9cc64800-0bf7-11eb-9eb8-b93ce6a6e02a.png){:class="img-responsive"}


### Results

We prove correctness, describe algorithm, show runtime, and demonstrate statistical robustness of our method in our paper.

Below, we compare the cell populations flagged comparing SpecEnr vs proportion. 

Data sets pos1, pos2, pos3 are synthetic positive controls we created where we increase the abundance of cell populations (A+), (A+B+C+), and (A+B+ and D+ hence A+B+D+) respectively.

[flowcap](https://doi.org/10.1038/nmeth.2365) and [pregnancy](https://doi.org/10.1126/sciimmunol.aan2946) are real data sets where we compare healthy vs AML positive patients, and women in their late term of pregnancy and 6 weeks post-partum. 

In both cases, SpecEnr was able to flag the driver cell populations and tell a story about how one can access these cell populations reminiscent of a top-down gating strategy.


![result](https://user-images.githubusercontent.com/22086811/95698799-9a63ee00-0bf7-11eb-8a64-8a8956a7c424.png){:class="img-responsive"}
