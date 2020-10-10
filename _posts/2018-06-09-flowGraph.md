---
title: "Yue, Alice, et al. "Identifying differential cell populations in flow cytometry data accounting for marker frequency." BioRxiv (2019): 837765."
date: 2020-09-30
categories: publications
excerpt_separator: <!--more-->
---

## Identifying maximal differential cellpopulations in flow cytometry data accounting for dependence between cell populations

Alice Yue, Cedric Chauve, Maxwell Libbrecht, Ryan Brinkman

[Paper](#) [Github](#) [Poster](#) [Presentation](#)

<!--more-->

We propose SpecEnr (specific enrichment), a cell population score that accounts for dependency between cell populations, and a method that harness SpecEnr properties to find candidate biomarkers for disease diagnosis in flow cytometry (FCM) data.

**Input**: For two class of FCM samples (e.g. control vs experiment), we take as input a vector for each sample. We refer to this vector as a sample. 
- A **sample** contains a cell count value for each cell population. This cell count is the number of cells in each cell population. 
- A **cell population** is a group of cells that does not/contain the the same set of markers. For example, cell population A+B+C- contans markers A and B but does not contain marker C. All samples contain the same cell populations.
- 
