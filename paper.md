---
title: 'MTSS: A CUDA software for the analysis of Multivariate Time Series'
tags:
- machine learning
- time series
- multivariate analysis
- classification
- subsequence similarity search
- GPU
- CUDA
authors:
 - name: Davide Nardone
   orcid: 0000-0003-0486-1791
   affiliation: "1"
affiliations:
 - name: Dept. of Science and Technology, University of Naples Parthenope
   index: 1
date: 14 September 2018
bibliography: paper.bib
---

# Summary
In these days, the alignment of multidimensional sequences is required in many fields such as bio-informatics, speech recognition, time-series analysis etc. The comparison of different time series is involved for discovering similarities and pattern in data. The most important involved tasks are: 1) *indexing* is process to identify the most similar time series in a dataset given a query time series; 2) *classification* is used to categorize data into predefined group [ref]; 3) *clustering* is an unsupervised categorization of data [ref]; 4) *anomaly detection* is the identification of abnormal or unique data items[ref]. For such tasks it is necessary to compare time series using an appropriate similarity measure[ref] which could not be very efficiently handled by using a traditional DTW, since it makes each pairwise alignment independently and cause each dimensions to be compared separately. Although these problems seem to be already solved in the state-of-art, almost all of them doesn't mention the problem to process these tasks on large amount of data in an reasonable amount of time. In this work, we propose a Multivariate Time Series Software (MTSS) software for speeding-up the above mentioned task.

MTSS is a GP-GPU Dynamic Time Warping (DTW) implementation for the analysis of Multivariate Time Series Object (MTSO). Since the warping of multidimensional time series either for the purpose of classification or sub-sequence comparing is a really time consuming task we developed a GP-GPU software for tackle down this problem. The platform used for this purpose is CUDA toolkit which is a parallel computing platform and programming model developed by NVIDIA for general computing on graphical processing units (GPUs). 
CUDA has its own device memory on the card and can ex-ecute many threads in parallel [22]. This architecture allows each DTW distance  to be computed in parallel on different segments  of  the  time  series.   Each  of  these  threads  is assigned an ID that's used to determine the memory addresses (i.e. the  segment  of  the  time  series)  it  should  operate on.  The hardware is free to determine the mapping and scheduling of these threads on the available processing cores. A thread block is defined as a batch of threads that are guaranteed to run simultaneously and cooperate with each other through shared resources. The size of a thread block can be specified at runtime.

The software is purely written in CUDA, using C language as support and can be used as a Standard Command Line Options style. It's mainly designed for the *Classification* and the *Subsequence Similarity Search* of MTSO. Originally inspired by [@sart2010accelerating], MTSS aims to improve the Time Performance and Accuracy for classifying and sub-searching any kind of MTSO by using the well known similarity measure: Dynamic Time Warping (DTW). MTSS drastically improves the time performance of these two tasks, achieving almost three order of magnitude of speedup, whilst getting better accuracy results. In order to do that, it uses different types of DTW, namely:

1. **D-MDTW:** Dependent-Multivariate Dynamic Time Warping
2. **I-MDTW:** Independent-Multivariate Dynamic Time Warping
3. **R-MDTW:** Rotation-Multivariate Dynamic Time Warping

The software 
For more information, please refer to [@sart2010accelerating-@shokoohi2015non].

# Examples

nvcc -D WS=421 MD_DTW.cu module.cu -o mdtwObj

./mdtwObj -t CLASSIFICATION -i GPU 3 512 1 -f X_MAT Y_MAT Z_MAT -k 10 -o 1000 152 DTW -m 0 -d 0

# References

# Acknowledgements
