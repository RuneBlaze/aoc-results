## Basic statistics of the CEN

```python
>>> from belinda import *
>>> g = Graph("cen.bincode.lz4")
>>> print(g)
Graph(n=13989436, m=92051051) #  n = 13989436, m = 92051051
```

## Links for Various Results

 - AOC+Leiden(CPM) on CEN
   - [r = 1e-1](#tables-for-centsvleiden_cpm_01)
   - [r = 1e-2](#tables-for-centsvleiden_cpm_001)
   - [r = 1e-3](#tables-for-centsvleiden_cpm_0001)
   - [r = 1e-4](#tables-for-centsvleiden_cpm_00001)
 - [AOC+Leiden(Mod) on CEN](#tables-for-centsvleiden_mod)
 - [AOC+IKC(k = 10) on CEN](#tables-for-centsvikc10_cleaned)

Also see the [resolution limit statement](#a-resolution-limit-statement-for-aoc-paired-with-cpm) for AOC+Leiden(CPM).

## Column names

 - `variant`: the subset of clusters that we are looking at
   - `everything`: all clusters including singletons
   - `everything_but_singletons`: `everything` removing all singleton clusters
   - `not_tree`: those that are not trees
   - `only_tree`: those that are trees, now including all singletons
   - `A+B`: both `A` and `B` applied
 - `augmented`: post-AOC (true) or pre-AOC
 - `Deviation from treeness`: `(m - n + 1 ) / n`
 - `% Non-singletons Augmented post-AOC`: percentage of *non-singleton* clusters that were augmented post-AOC of the shown pre-AOC clusters
 - `Relative Increase in Size post-AOC`: distribution of `new_size/old_size - 1` for non-singleton clusters

Distributions are written in minimum, median, maximum format.

## A resolution limit statement for AOC paired with CPM

Assume $G = (V, E)$ as the background network. Assume $G$ is connected. Consider a cluster $K_i$ to be augmented
by AOC using the CPM criterion, with resolution value $\gamma$ for AOC (the original clustering can be arbitrary).
Let $n$ be the number of nodes in $K_i$ and $m$ the number of edges in $K_i$. Assume $n < 10^5$ and $|V| > 10^5$. Note that $K_i$ is extremely arbitrary -- we so far imposed few constraints on $K_i$. We now show that $K_i$ post AOC has an arguably undesirable size lower-bound.

> **Theorem**: if $\gamma = 0.01$, $K_i$ after AOC augmentation will have size $\geq 101$. That is, clusters below size $101$
> will never be detected by AOC. Moreover, if $\gamma = 0.0001$, $K_i$ after AOC augmentation will have size $\geq 10001$ **(!)**.

Proof omitted due to time constraints. Note that when $\gamma = 0.0001$, $K_i$ drawn from the CPM+Leiden cluster
distributions on CEN before AOC has median size 380. That is,
at least half of the clusters will be bloated to size $\geq 10001$ post AOC.

A stronger form of the above statement:

> **Theorem**: if $\gamma = 0.01$, consider an input cluster $K_i$, during AOC+CPM, as long as $K_i$ has size $\leq 101$, $K_i$ can be augmented with any node that is connected to $K_i$.


## Tables for `cen.tsv.leiden_cpm_0.1`

| Variant             | Augmented   |   # Non-singleton Clusters |   # Singletons | % Non-singletons Augmented post-AOC   | Relative Increase in Size post-AOC   |   Node Coverage (%) |   Edge Coverage (%) | Modularity                  | MCD                       | Clusters Per Node         | CPM                       | Size                      | Deviation from Treeness   | Density                   |
|---------------------|-------------|--------------|----------------|---------------|-----------------------------|---------------------|---------------------|-----------------------------|---------------------------|---------------------------|---------------------------|---------------------------|---------------------------|---------------------------|
| everything                 | False       |       516922 |        8336638 | 0.0           | 0.0E+00, 0.0E+00, 0.0E+00   |               100   |                 9.6 | -5.6E-08, -3.0E-17, 1.3E-04 | 0.0E+00, 0.0E+00, 3.3E+01 | -                         | 0.0E+00, 0.0E+00, 6.5E+03 | 1.0E+00, 1.0E+00, 3.2E+02 | 0.0E+00, 0.0E+00, 3.5E+01 | 1.4E-01, 1.9E-01, 1.0E+00 |
| everything                 | True        |       516922 |        8336638 | -             | -                           |               100   |                 9.6 | -5.6E-08, -3.0E-17, 1.3E-04 | 0.0E+00, 0.0E+00, 3.3E+01 | 1.0E+00, 1.0E+00, 1.0E+00 | 0.0E+00, 0.0E+00, 6.5E+03 | 1.0E+00, 1.0E+00, 3.2E+02 | 0.0E+00, 0.0E+00, 3.5E+01 | 1.4E-01, 1.9E-01, 1.0E+00 |
| everything_but_singletons    | False       |       516922 |              0 | 0.0           | 0.0E+00, 0.0E+00, 0.0E+00   |                40.4 |                 9.6 | -5.6E-08, 1.1E-07, 1.3E-04  | 1.0E+00, 1.0E+00, 3.3E+01 | -                         | 9.0E-01, 4.5E+00, 6.5E+03 | 2.0E+00, 1.1E+01, 3.2E+02 | 0.0E+00, 0.0E+00, 3.5E+01 | 1.4E-01, 1.9E-01, 1.0E+00 |
| everything_but_singletons    | True        |       516922 |              0 | -             | -                           |                40.4 |                 9.6 | -5.6E-08, 1.1E-07, 1.3E-04  | 1.0E+00, 1.0E+00, 3.3E+01 | 1.0E+00, 1.0E+00, 1.0E+00 | 9.0E-01, 4.5E+00, 6.5E+03 | 2.0E+00, 1.1E+01, 3.2E+02 | 0.0E+00, 0.0E+00, 3.5E+01 | 1.4E-01, 1.9E-01, 1.0E+00 |
| size_ge_11          | False       |       275193 |              0 | 0.0           | 0.0E+00, 0.0E+00, 0.0E+00   |                24.1 |                 7.4 | -5.6E-08, 1.1E-07, 1.3E-04  | 1.0E+00, 1.0E+00, 3.3E+01 | -                         | 4.5E+00, 4.5E+00, 6.5E+03 | 1.1E+01, 1.1E+01, 3.2E+02 | 0.0E+00, 0.0E+00, 3.5E+01 | 1.4E-01, 1.8E-01, 5.9E-01 |
| size_ge_11          | True        |       275193 |              0 | -             | -                           |                24.1 |                 7.4 | -5.6E-08, 1.1E-07, 1.3E-04  | 1.0E+00, 1.0E+00, 3.3E+01 | 1.0E+00, 1.0E+00, 1.0E+00 | 4.5E+00, 4.5E+00, 6.5E+03 | 1.1E+01, 1.1E+01, 3.2E+02 | 0.0E+00, 0.0E+00, 3.5E+01 | 1.4E-01, 1.8E-01, 5.9E-01 |
| not_tree            | False       |        21483 |              0 | 0.0           | 0.0E+00, 0.0E+00, 0.0E+00   |                 4.1 |                 4.6 | 3.3E-08, 3.6E-07, 1.3E-04   | 1.0E+00, 2.0E+00, 3.3E+01 | -                         | 2.7E+00, 1.7E+01, 6.5E+03 | 3.0E+00, 1.8E+01, 3.2E+02 | 9.1E-02, 8.5E-01, 3.5E+01 | 1.4E-01, 2.5E-01, 1.0E+00 |
| not_tree            | True        |        21483 |              0 | -             | -                           |                 4.1 |                 4.6 | 3.3E-08, 3.6E-07, 1.3E-04   | 1.0E+00, 2.0E+00, 3.3E+01 | 1.0E+00, 1.0E+00, 1.0E+00 | 2.7E+00, 1.7E+01, 6.5E+03 | 3.0E+00, 1.8E+01, 3.2E+02 | 9.1E-02, 8.5E-01, 3.5E+01 | 1.4E-01, 2.5E-01, 1.0E+00 |
| not_tree+size_ge_11 | False       |        18579 |              0 | 0.0           | 0.0E+00, 0.0E+00, 0.0E+00   |                 3.9 |                 4.6 | 1.2E-07, 3.9E-07, 1.3E-04   | 1.0E+00, 2.0E+00, 3.3E+01 | -                         | 5.5E+00, 1.7E+01, 6.5E+03 | 1.1E+01, 1.9E+01, 3.2E+02 | 9.1E-02, 8.6E-01, 3.5E+01 | 1.4E-01, 2.5E-01, 5.9E-01 |
| not_tree+size_ge_11 | True        |        18579 |              0 | -             | -                           |                 3.9 |                 4.6 | 1.2E-07, 3.9E-07, 1.3E-04   | 1.0E+00, 2.0E+00, 3.3E+01 | 1.0E+00, 1.0E+00, 1.0E+00 | 5.5E+00, 1.7E+01, 6.5E+03 | 1.1E+01, 1.9E+01, 3.2E+02 | 9.1E-02, 8.6E-01, 3.5E+01 | 1.4E-01, 2.5E-01, 5.9E-01 |
| only_tree           | False       |       495439 |        8336638 | 0.0           | 0.0E+00, 0.0E+00, 0.0E+00   |                95.9 |                 5   | -5.6E-08, -3.0E-17, 1.1E-07 | 0.0E+00, 0.0E+00, 1.0E+00 | -                         | 0.0E+00, 0.0E+00, 4.5E+00 | 1.0E+00, 1.0E+00, 1.1E+01 | 0.0E+00, 0.0E+00, 0.0E+00 | 1.8E-01, 1.8E-01, 1.0E+00 |
| only_tree           | True        |       495439 |        8336638 | -             | -                           |                95.9 |                 5   | -5.6E-08, -3.0E-17, 1.1E-07 | 0.0E+00, 0.0E+00, 1.0E+00 | 1.0E+00, 1.0E+00, 1.0E+00 | 0.0E+00, 0.0E+00, 4.5E+00 | 1.0E+00, 1.0E+00, 1.1E+01 | 0.0E+00, 0.0E+00, 0.0E+00 | 1.8E-01, 1.8E-01, 1.0E+00 |
## Tables for `cen.tsv.leiden_cpm_0.01`

| Variant             | Augmented   |   # Non-singleton Clusters |   # Singletons | % Non-singletons Augmented post-AOC   | Relative Increase in Size post-AOC   |   Node Coverage (%) |   Edge Coverage (%) | Modularity                  | MCD                       | Clusters Per Node         | CPM                       | Size                      | Deviation from Treeness   | Density                   |
|---------------------|-------------|--------------|----------------|---------------|-----------------------------|---------------------|---------------------|-----------------------------|---------------------------|---------------------------|---------------------------|---------------------------|---------------------------|---------------------------|
| everything                 | False       |       280229 |        3243923 | 93.9          | 0.0E+00, 4.9E+00, 1.6E+01   |               100   |                24.4 | -8.6E-07, -3.0E-17, 1.6E-03 | 0.0E+00, 0.0E+00, 3.5E+01 | -                         | 0.0E+00, 0.0E+00, 9.0E+04 | 1.0E+00, 1.0E+00, 3.3E+03 | 0.0E+00, 0.0E+00, 4.3E+01 | 1.9E-02, 7.5E-02, 1.0E+00 |
| everything                 | True        |       280229 |        3243081 | -             | -                           |               100   |                25   | -6.3E-05, -3.0E-17, 1.6E-03 | 0.0E+00, 0.0E+00, 3.5E+01 | 1.0E+00, 1.0E+00, 2.5E+05 | 0.0E+00, 0.0E+00, 9.0E+04 | 1.0E+00, 1.0E+00, 3.3E+03 | 0.0E+00, 0.0E+00, 4.3E+01 | 1.1E-02, 1.2E-02, 1.0E+00 |
| everything_but_singletons    | False       |       280229 |              0 | 93.9          | 0.0E+00, 4.9E+00, 1.6E+01   |                76.8 |                24.4 | -8.6E-07, 3.0E-07, 1.6E-03  | 1.0E+00, 1.0E+00, 3.5E+01 | -                         | 9.9E-01, 2.4E+01, 9.0E+04 | 2.0E+00, 2.8E+01, 3.3E+03 | 0.0E+00, 0.0E+00, 4.3E+01 | 1.9E-02, 7.5E-02, 1.0E+00 |
| everything_but_singletons    | True        |       280229 |              0 | -             | -                           |                76.8 |                25   | -6.3E-05, -2.8E-05, 1.6E-03 | 1.0E+00, 1.0E+00, 3.5E+01 | 1.0E+00, 1.0E+00, 2.5E+05 | 9.9E-01, 2.4E+01, 9.0E+04 | 2.0E+00, 1.7E+02, 3.3E+03 | 0.0E+00, 0.0E+00, 4.3E+01 | 1.1E-02, 1.2E-02, 1.0E+00 |
| size_ge_11          | False       |       275415 |              0 | 95.5          | 0.0E+00, 5.2E+00, 1.6E+01   |                76.5 |                24.4 | -8.6E-07, 3.2E-07, 1.6E-03  | 1.0E+00, 1.0E+00, 3.5E+01 | -                         | 9.4E+00, 2.5E+01, 9.0E+04 | 1.1E+01, 2.8E+01, 3.3E+03 | 0.0E+00, 0.0E+00, 4.3E+01 | 1.9E-02, 7.4E-02, 3.1E-01 |
| size_ge_11          | True        |       275415 |              0 | -             | -                           |                76.5 |                24.9 | -6.3E-05, -2.9E-05, 1.6E-03 | 1.0E+00, 1.0E+00, 3.5E+01 | 1.0E+00, 1.0E+00, 2.5E+05 | 9.4E+00, 2.5E+01, 9.0E+04 | 1.1E+01, 1.7E+02, 3.3E+03 | 0.0E+00, 0.0E+00, 4.3E+01 | 1.1E-02, 1.2E-02, 2.1E-01 |
| not_tree            | False       |        64611 |              0 | 92.6          | 0.0E+00, 3.9E+00, 1.6E+01   |                24.9 |                16.8 | 3.3E-08, 4.7E-07, 1.6E-03   | 1.0E+00, 1.0E+00, 3.5E+01 | -                         | 3.0E+00, 3.7E+01, 9.0E+04 | 3.0E+00, 3.4E+01, 3.3E+03 | 9.9E-03, 2.8E-01, 4.3E+01 | 1.9E-02, 7.7E-02, 1.0E+00 |
| not_tree            | True        |        64617 |              0 | -             | -                           |                24.9 |                16.9 | -6.0E-05, -2.6E-05, 1.6E-03 | 1.0E+00, 1.0E+00, 3.5E+01 | 1.0E+00, 1.0E+00, 5.8E+04 | 3.0E+00, 3.8E+01, 9.0E+04 | 3.0E+00, 1.7E+02, 3.3E+03 | 5.3E-03, 5.7E-02, 4.3E+01 | 1.1E-02, 1.3E-02, 1.0E+00 |
| not_tree+size_ge_11 | False       |        64538 |              0 | 92.7          | 0.0E+00, 3.9E+00, 1.6E+01   |                24.9 |                16.8 | 1.2E-07, 4.7E-07, 1.6E-03   | 1.0E+00, 1.0E+00, 3.5E+01 | -                         | 1.0E+01, 3.7E+01, 9.0E+04 | 1.1E+01, 3.4E+01, 3.3E+03 | 9.9E-03, 2.8E-01, 4.3E+01 | 1.9E-02, 7.7E-02, 3.1E-01 |
| not_tree+size_ge_11 | True        |        64544 |              0 | -             | -                           |                24.9 |                16.9 | -6.0E-05, -2.6E-05, 1.6E-03 | 1.0E+00, 1.0E+00, 3.5E+01 | 1.0E+00, 1.0E+00, 5.8E+04 | 9.6E+00, 3.8E+01, 9.0E+04 | 1.2E+01, 1.7E+02, 3.3E+03 | 5.3E-03, 5.7E-02, 4.3E+01 | 1.1E-02, 1.3E-02, 2.1E-01 |
| only_tree           | False       |       215618 |        3243923 | 94.3          | 0.0E+00, 5.4E+00, 1.6E+01   |                75.1 |                 7.7 | -8.6E-07, -3.0E-17, 1.1E-06 | 0.0E+00, 0.0E+00, 1.0E+00 | -                         | 0.0E+00, 0.0E+00, 5.0E+01 | 1.0E+00, 1.0E+00, 1.0E+02 | 0.0E+00, 0.0E+00, 0.0E+00 | 2.0E-02, 7.4E-02, 1.0E+00 |
| only_tree           | True        |       215612 |        3243081 | -             | -                           |                75.2 |                 8.1 | -6.3E-05, -3.0E-17, 1.8E-06 | 0.0E+00, 0.0E+00, 1.0E+00 | 1.0E+00, 1.0E+00, 2.0E+05 | 0.0E+00, 0.0E+00, 5.0E+01 | 1.0E+00, 1.0E+00, 1.9E+02 | 0.0E+00, 0.0E+00, 0.0E+00 | 1.1E-02, 1.1E-02, 1.0E+00 |
## Tables for `cen.tsv.leiden_cpm_0.001`

| Variant             | Augmented   |   # Non-singleton Clusters |   # Singletons | % Non-singletons Augmented post-AOC   | Relative Increase in Size post-AOC   |   Node Coverage (%) |   Edge Coverage (%) | Modularity                  | MCD                       | Clusters Per Node         | CPM                       | Size                      | Deviation from Treeness   | Density                   |
|---------------------|-------------|--------------|----------------|---------------|-----------------------------|---------------------|---------------------|-----------------------------|---------------------------|---------------------------|---------------------------|---------------------------|---------------------------|---------------------------|
| everything                 | False       |        66410 |        2180745 | 96.9          | 0.0E+00, 1.8E+01, 1.8E+02   |               100   |                39.1 | -2.8E-14, -3.0E-17, 6.3E-03 | 0.0E+00, 0.0E+00, 1.8E+01 | -                         | 0.0E+00, 0.0E+00, 4.4E+05 | 1.0E+00, 1.0E+00, 1.8E+04 | 0.0E+00, 0.0E+00, 3.2E+01 | 2.0E-03, 2.3E-02, 1.0E+00 |
| everything                 | True        |        66410 |        2180328 | -             | -                           |               100   |                39.4 | -2.2E-04, -3.0E-17, 6.3E-03 | 0.0E+00, 0.0E+00, 1.8E+01 | 1.0E+00, 1.0E+00, 6.4E+04 | 0.0E+00, 0.0E+00, 4.4E+05 | 1.0E+00, 1.0E+00, 1.8E+04 | 0.0E+00, 0.0E+00, 3.2E+01 | 1.0E-03, 1.1E-03, 1.0E+00 |
| everything_but_singletons    | False       |        66410 |              0 | 96.9          | 0.0E+00, 1.8E+01, 1.8E+02   |                84.4 |                39.1 | 1.1E-08, 1.1E-06, 6.3E-03   | 1.0E+00, 1.0E+00, 1.8E+01 | -                         | 1.0E+00, 9.9E+01, 4.4E+05 | 2.0E+00, 9.6E+01, 1.8E+04 | 0.0E+00, 4.2E-02, 3.2E+01 | 2.0E-03, 2.3E-02, 1.0E+00 |
| everything_but_singletons    | True        |        66410 |              0 | -             | -                           |                84.4 |                39.4 | -2.2E-04, -1.4E-04, 6.3E-03 | 1.0E+00, 1.0E+00, 1.8E+01 | 1.0E+00, 1.0E+00, 6.4E+04 | 1.0E+00, 1.0E+02, 4.4E+05 | 2.0E+00, 1.9E+03, 1.8E+04 | 0.0E+00, 1.7E-03, 3.2E+01 | 1.0E-03, 1.1E-03, 1.0E+00 |
| size_ge_11          | False       |        65836 |              0 | 97.7          | 0.0E+00, 1.9E+01, 1.8E+02   |                84.4 |                39.1 | 1.1E-07, 1.1E-06, 6.3E-03   | 1.0E+00, 1.0E+00, 1.8E+01 | -                         | 9.9E+00, 1.0E+02, 4.4E+05 | 1.1E+01, 9.7E+01, 1.8E+04 | 0.0E+00, 4.3E-02, 3.2E+01 | 2.0E-03, 2.3E-02, 2.3E-01 |
| size_ge_11          | True        |        65836 |              0 | -             | -                           |                84.4 |                39.4 | -2.2E-04, -1.4E-04, 6.3E-03 | 1.0E+00, 1.0E+00, 1.8E+01 | 1.0E+00, 1.0E+00, 6.4E+04 | 9.9E+00, 1.0E+02, 4.4E+05 | 1.1E+01, 1.9E+03, 1.8E+04 | 0.0E+00, 2.1E-03, 3.2E+01 | 1.0E-03, 1.1E-03, 2.1E-01 |
| not_tree            | False       |        42845 |              0 | 97.7          | 0.0E+00, 1.6E+01, 1.4E+02   |                62.1 |                35.8 | 4.3E-08, 1.4E-06, 6.3E-03   | 1.0E+00, 1.0E+00, 1.8E+01 | -                         | 4.0E+00, 1.2E+02, 4.4E+05 | 4.0E+00, 1.1E+02, 1.8E+04 | 2.0E-03, 1.3E-01, 3.2E+01 | 2.4E-03, 2.1E-02, 6.7E-01 |
| not_tree            | True        |        42848 |              0 | -             | -                           |                62.1 |                36   | -2.2E-04, -1.4E-04, 6.3E-03 | 1.0E+00, 1.0E+00, 1.8E+01 | 1.0E+00, 1.0E+00, 4.2E+04 | 4.0E+00, 1.2E+02, 4.4E+05 | 4.0E+00, 1.9E+03, 1.8E+04 | 5.0E-04, 7.2E-03, 3.2E+01 | 1.0E-03, 1.1E-03, 6.7E-01 |
| not_tree+size_ge_11 | False       |        42840 |              0 | 97.7          | 0.0E+00, 1.6E+01, 1.4E+02   |                62.1 |                35.8 | 1.5E-07, 1.4E-06, 6.3E-03   | 1.0E+00, 1.0E+00, 1.8E+01 | -                         | 1.4E+01, 1.2E+02, 4.4E+05 | 1.2E+01, 1.1E+02, 1.8E+04 | 2.0E-03, 1.3E-01, 3.2E+01 | 2.4E-03, 2.1E-02, 2.3E-01 |
| not_tree+size_ge_11 | True        |        42843 |              0 | -             | -                           |                62.1 |                36   | -2.2E-04, -1.4E-04, 6.3E-03 | 1.0E+00, 1.0E+00, 1.8E+01 | 1.0E+00, 1.0E+00, 4.2E+04 | 1.0E+01, 1.2E+02, 4.4E+05 | 1.2E+01, 1.9E+03, 1.8E+04 | 5.0E-04, 7.2E-03, 3.2E+01 | 1.0E-03, 1.1E-03, 2.1E-01 |
| only_tree           | False       |        23565 |        2180745 | 95.4          | 0.0E+00, 2.8E+01, 1.8E+02   |                37.9 |                 3.4 | -2.8E-14, -3.0E-17, 1.1E-05 | 0.0E+00, 0.0E+00, 1.0E+00 | -                         | 0.0E+00, 0.0E+00, 5.0E+02 | 1.0E+00, 1.0E+00, 1.0E+03 | 0.0E+00, 0.0E+00, 0.0E+00 | 2.0E-03, 3.1E-02, 1.0E+00 |
| only_tree           | True        |        23562 |        2180328 | -             | -                           |                38   |                 3.5 | -2.1E-04, -3.0E-17, 1.1E-05 | 0.0E+00, 0.0E+00, 1.0E+00 | 1.0E+00, 1.0E+00, 2.2E+04 | 0.0E+00, 0.0E+00, 5.0E+02 | 1.0E+00, 1.0E+00, 2.0E+03 | 0.0E+00, 0.0E+00, 0.0E+00 | 1.0E-03, 1.0E-03, 1.0E+00 |
## Tables for `cen.tsv.leiden_cpm_0.0001`

| Variant             | Augmented   |   # Non-singleton Clusters |   # Singletons | % Non-singletons Augmented post-AOC   | Relative Increase in Size post-AOC   |   Node Coverage (%) |   Edge Coverage (%) | Modularity                  | MCD                       | Clusters Per Node         | CPM                       | Size                      | Deviation from Treeness   | Density                   |
|---------------------|-------------|--------------|----------------|---------------|-----------------------------|---------------------|---------------------|-----------------------------|---------------------------|---------------------------|---------------------------|---------------------------|---------------------------|---------------------------|
| everything                 | False       |        11829 |        1303375 | 94.3          | 0.0E+00, 4.5E+01, 1.8E+03   |               100   |                51.7 | -7.6E-15, -3.0E-17, 1.7E-02 | 0.0E+00, 0.0E+00, 7.0E+00 | -                         | 0.0E+00, 0.0E+00, 1.4E+06 | 1.0E+00, 1.0E+00, 7.0E+04 | 0.0E+00, 0.0E+00, 2.3E+01 | 2.0E-04, 6.0E-03, 1.0E+00 |
| everything                 | True        |        11829 |        1301956 | -             | -                           |               100   |                51.9 | -3.7E-04, -3.0E-17, 1.7E-02 | 0.0E+00, 0.0E+00, 7.0E+00 | 1.0E+00, 1.0E+00, 1.1E+04 | 0.0E+00, 0.0E+00, 1.4E+06 | 1.0E+00, 1.0E+00, 7.0E+04 | 0.0E+00, 0.0E+00, 2.3E+01 | 1.0E-04, 1.0E-04, 1.0E+00 |
| everything_but_singletons    | False       |        11829 |              0 | 94.3          | 0.0E+00, 4.5E+01, 1.8E+03   |                90.7 |                51.7 | 1.1E-08, 4.6E-06, 1.7E-02   | 1.0E+00, 1.0E+00, 7.0E+00 | -                         | 1.0E+00, 4.2E+02, 1.4E+06 | 2.0E+00, 3.8E+02, 7.0E+04 | 0.0E+00, 9.4E-02, 2.3E+01 | 2.0E-04, 6.0E-03, 1.0E+00 |
| everything_but_singletons    | True        |        11829 |              0 | -             | -                           |                90.7 |                51.9 | -3.7E-04, -2.1E-04, 1.7E-02 | 1.0E+00, 1.0E+00, 7.0E+00 | 1.0E+00, 1.0E+00, 1.1E+04 | 1.0E+00, 4.2E+02, 1.4E+06 | 2.0E+00, 2.0E+04, 7.0E+04 | 0.0E+00, 1.6E-03, 2.3E+01 | 1.0E-04, 1.0E-04, 1.0E+00 |
| size_ge_11          | False       |        11381 |              0 | 98.0          | 0.0E+00, 4.8E+01, 1.8E+03   |                90.7 |                51.7 | 1.1E-07, 5.0E-06, 1.7E-02   | 1.0E+00, 1.0E+00, 7.0E+00 | -                         | 1.0E+01, 4.5E+02, 1.4E+06 | 1.1E+01, 4.0E+02, 7.0E+04 | 0.0E+00, 1.0E-01, 2.3E+01 | 2.0E-04, 5.8E-03, 2.3E-01 |
| size_ge_11          | True        |        11381 |              0 | -             | -                           |                90.7 |                51.9 | -3.7E-04, -2.1E-04, 1.7E-02 | 1.0E+00, 1.0E+00, 7.0E+00 | 1.0E+00, 1.0E+00, 1.1E+04 | 1.0E+01, 4.5E+02, 1.4E+06 | 1.1E+01, 2.0E+04, 7.0E+04 | 0.0E+00, 1.8E-03, 2.3E+01 | 1.0E-04, 1.0E-04, 2.1E-01 |
| not_tree            | False       |         9534 |              0 | 98.1          | 0.0E+00, 4.1E+01, 1.8E+03   |                81.2 |                50.2 | 3.3E-08, 5.9E-06, 1.7E-02   | 1.0E+00, 1.0E+00, 7.0E+00 | -                         | 3.0E+00, 5.3E+02, 1.4E+06 | 3.0E+00, 4.6E+02, 7.0E+04 | 3.8E-04, 1.4E-01, 2.3E+01 | 2.8E-04, 5.1E-03, 1.0E+00 |
| not_tree            | True        |         9537 |              0 | -             | -                           |                81.2 |                50.5 | -3.7E-04, -2.0E-04, 1.7E-02 | 1.0E+00, 1.0E+00, 7.0E+00 | 1.0E+00, 1.0E+00, 9.3E+03 | 3.0E+00, 5.3E+02, 1.4E+06 | 3.0E+00, 2.0E+04, 7.0E+04 | 5.0E-05, 3.1E-03, 2.3E+01 | 1.0E-04, 1.0E-04, 1.0E+00 |
| not_tree+size_ge_11 | False       |         9528 |              0 | 98.2          | 0.0E+00, 4.1E+01, 1.8E+03   |                81.2 |                50.2 | 1.2E-07, 5.9E-06, 1.7E-02   | 1.0E+00, 1.0E+00, 7.0E+00 | -                         | 1.1E+01, 5.3E+02, 1.4E+06 | 1.1E+01, 4.6E+02, 7.0E+04 | 3.8E-04, 1.4E-01, 2.3E+01 | 2.8E-04, 5.1E-03, 2.3E-01 |
| not_tree+size_ge_11 | True        |         9531 |              0 | -             | -                           |                81.2 |                50.5 | -3.7E-04, -2.0E-04, 1.7E-02 | 1.0E+00, 1.0E+00, 7.0E+00 | 1.0E+00, 1.0E+00, 9.3E+03 | 1.0E+01, 5.3E+02, 1.4E+06 | 1.2E+01, 2.0E+04, 7.0E+04 | 5.0E-05, 3.1E-03, 2.3E+01 | 1.0E-04, 1.0E-04, 2.1E-01 |
| only_tree           | False       |         2295 |        1303375 | 78.3          | 0.0E+00, 1.2E+02, 1.8E+03   |                18.8 |                 1.4 | -7.6E-15, -3.0E-17, 1.1E-04 | 0.0E+00, 0.0E+00, 1.0E+00 | -                         | 0.0E+00, 0.0E+00, 5.0E+03 | 1.0E+00, 1.0E+00, 1.0E+04 | 0.0E+00, 0.0E+00, 0.0E+00 | 2.0E-04, 2.2E-02, 1.0E+00 |
| only_tree           | True        |         2292 |        1301956 | -             | -                           |                19   |                 1.5 | -3.7E-04, -3.0E-17, 1.1E-04 | 0.0E+00, 0.0E+00, 1.0E+00 | 1.0E+00, 1.0E+00, 1.8E+03 | 0.0E+00, 0.0E+00, 5.0E+03 | 1.0E+00, 1.0E+00, 2.0E+04 | 0.0E+00, 0.0E+00, 0.0E+00 | 1.0E-04, 1.0E-04, 1.0E+00 |

## Tables for `cen.tsv.leiden_mod`

| Variant             | Augmented   |   # Non-singleton Clusters |   # Singletons | % Non-singletons Augmented post-AOC   | Relative Increase in Size post-AOC   |   Node Coverage (%) |   Edge Coverage (%) | Modularity                | MCD                       | Clusters Per Node         | CPM   | Size                      | Deviation from Treeness   | Density                   |
|---------------------|-------------|--------------|----------------|---------------|-----------------------------|---------------------|---------------------|---------------------------|---------------------------|---------------------------|-------|---------------------------|---------------------------|---------------------------|
| everything                 | False       |          257 |              0 | 62.3          | 0.0E+00, 1.3E+03, 1.2E+06   |               100   |                72.3 | 1.1E-08, 3.6E-07, 6.7E-02 | 1.0E+00, 1.0E+00, 1.0E+00 | -                         | -     | 2.0E+00, 3.4E+01, 1.3E+06 | 0.0E+00, 0.0E+00, 7.3E+00 | 4.2E-06, 5.9E-02, 1.0E+00 |
| everything                 | True        |          257 |              0 | -             | -                           |               100   |               100   | 1.1E-08, 1.5E-05, 6.7E-02 | 1.0E+00, 1.0E+00, 1.0E+00 | 1.0E+00, 1.6E+02, 1.6E+02 | -     | 2.0E+00, 1.4E+07, 1.4E+07 | 0.0E+00, 5.6E+00, 6.3E+00 | 9.4E-07, 9.4E-07, 1.0E+00 |
| everything_but_singletons    | False       |          257 |              0 | 62.3          | 0.0E+00, 1.3E+03, 1.2E+06   |               100   |                72.3 | 1.1E-08, 3.6E-07, 6.7E-02 | 1.0E+00, 1.0E+00, 1.0E+00 | -                         | -     | 2.0E+00, 3.4E+01, 1.3E+06 | 0.0E+00, 0.0E+00, 7.3E+00 | 4.2E-06, 5.9E-02, 1.0E+00 |
| everything_but_singletons    | True        |          257 |              0 | -             | -                           |               100   |               100   | 1.1E-08, 1.5E-05, 6.7E-02 | 1.0E+00, 1.0E+00, 1.0E+00 | 1.0E+00, 1.6E+02, 1.6E+02 | -     | 2.0E+00, 1.4E+07, 1.4E+07 | 0.0E+00, 5.6E+00, 6.3E+00 | 9.4E-07, 9.4E-07, 1.0E+00 |
| size_ge_11          | False       |          193 |              0 | 82.9          | 0.0E+00, 1.1E+05, 1.2E+06   |               100   |                72.3 | 1.1E-07, 6.1E-07, 6.7E-02 | 1.0E+00, 1.0E+00, 1.0E+00 | -                         | -     | 1.1E+01, 5.7E+01, 1.3E+06 | 0.0E+00, 0.0E+00, 7.3E+00 | 4.2E-06, 3.5E-02, 2.1E-01 |
| size_ge_11          | True        |          193 |              0 | -             | -                           |               100   |               100   | 1.1E-07, 1.6E-05, 6.7E-02 | 1.0E+00, 1.0E+00, 1.0E+00 | 1.0E+00, 1.6E+02, 1.6E+02 | -     | 1.1E+01, 1.4E+07, 1.4E+07 | 0.0E+00, 5.6E+00, 6.3E+00 | 9.4E-07, 9.4E-07, 2.1E-01 |
| not_tree            | False       |           56 |              0 | 98.2          | 0.0E+00, 1.6E+02, 2.1E+05   |                99.9 |                72.3 | 1.5E-07, 9.0E-04, 6.7E-02 | 1.0E+00, 1.0E+00, 1.0E+00 | -                         | -     | 1.2E+01, 6.1E+04, 1.3E+06 | 1.9E-03, 6.3E-01, 7.3E+00 | 4.2E-06, 9.0E-05, 2.1E-01 |
| not_tree            | True        |          161 |              0 | -             | -                           |               100   |               100   | 1.5E-07, 1.6E-05, 6.7E-02 | 1.0E+00, 1.0E+00, 1.0E+00 | 1.0E+00, 1.6E+02, 1.6E+02 | -     | 1.2E+01, 1.4E+07, 1.4E+07 | 2.5E-01, 5.6E+00, 6.3E+00 | 9.4E-07, 9.4E-07, 2.1E-01 |
| not_tree+size_ge_11 | False       |           56 |              0 | 98.2          | 0.0E+00, 1.6E+02, 2.1E+05   |                99.9 |                72.3 | 1.5E-07, 9.0E-04, 6.7E-02 | 1.0E+00, 1.0E+00, 1.0E+00 | -                         | -     | 1.2E+01, 6.1E+04, 1.3E+06 | 1.9E-03, 6.3E-01, 7.3E+00 | 4.2E-06, 9.0E-05, 2.1E-01 |
| not_tree+size_ge_11 | True        |          161 |              0 | -             | -                           |               100   |               100   | 1.5E-07, 1.6E-05, 6.7E-02 | 1.0E+00, 1.0E+00, 1.0E+00 | 1.0E+00, 1.6E+02, 1.6E+02 | -     | 1.2E+01, 1.4E+07, 1.4E+07 | 2.5E-01, 5.6E+00, 6.3E+00 | 9.4E-07, 9.4E-07, 2.1E-01 |
| only_tree           | False       |          201 |              0 | 52.2          | 0.0E+00, 8.2E+04, 1.2E+06   |                 0.1 |                 0   | 1.1E-08, 2.1E-07, 1.1E-05 | 1.0E+00, 1.0E+00, 1.0E+00 | -                         | -     | 2.0E+00, 2.0E+01, 1.1E+03 | 0.0E+00, 0.0E+00, 0.0E+00 | 1.9E-03, 1.0E-01, 1.0E+00 |
| only_tree           | True        |           96 |              0 | -             | -                           |                 0   |                 0   | 1.1E-08, 6.0E-08, 6.1E-07 | 1.0E+00, 1.0E+00, 1.0E+00 | 1.0E+00, 1.0E+00, 1.0E+00 | -     | 2.0E+00, 6.5E+00, 5.7E+01 | 0.0E+00, 0.0E+00, 0.0E+00 | 3.5E-02, 3.1E-01, 1.0E+00 |

Sizes of the top 30 post-AOC clusters by size:
```json
13987937, 13987938, 13987939, 13987945, 13987945, 13987946, 13987951, 13987960, 13987964, 13987969, 13987975, 13987978, 13987982, 13987983, 13987985, 13987989, 13987990, 13987992, 13987993, 13987993, 13987996, 13987997, 13988000, 13988007, 13988012, 13988017, 13988019, 13988022, 13988022, 13988024, 13988031, 13988032, 13988034, 13988042, 13988043, 13988049, 13988050, 13988059, 13988060, 13988069, 13988069, 13988081, 13988081, 13988083, 13988087, 13988091, 13988105, 13988113, 13988120, 13988157
```

## Tables for `cen.tsv.ikc10_cleaned`

| Variant             | Augmented   |   # Non-singleton Clusters |   # Singletons | % Non-singletons Augmented post-AOC   | Relative Increase in Size post-AOC   |   Node Coverage (%) |   Edge Coverage (%) | Modularity                   | MCD                       | Clusters Per Node         | CPM   | Size                      | Deviation from Treeness   | Density                   |
|---------------------|-------------|--------------|----------------|---------------|-----------------------------|---------------------|---------------------|------------------------------|---------------------------|---------------------------|-------|---------------------------|---------------------------|---------------------------|
| everything                 | False       |          128 |       13454271 | 74.2          | 0.0E+00, 3.2E-02, 4.1E-01   |               100   |                11.8 | -1.0E-08, -1.2E-16, 1.7E-02  | 0.0E+00, 0.0E+00, 5.3E+01 | -                         | -     | 1.0E+00, 1.0E+00, 2.1E+05 | 0.0E+00, 0.0E+00, 4.8E+01 | 1.2E-04, 3.3E-01, 9.1E-01 |
| everything                 | True        |          128 |       13454271 | -             | -                           |               100   |                18   | -1.0E-08, -1.2E-16, 7.4E-03  | 0.0E+00, 0.0E+00, 5.3E+01 | 1.0E+00, 1.0E+00, 1.8E+01 | -     | 1.0E+00, 1.0E+00, 2.9E+05 | 0.0E+00, 0.0E+00, 4.8E+01 | 1.9E-04, 3.4E-01, 8.8E-01 |
| everything_but_singletons    | False       |          128 |              0 | 74.2          | 0.0E+00, 3.2E-02, 4.1E-01   |                 3.8 |                11.8 | 8.5E-07, 1.1E-05, 1.7E-02    | 1.0E+01, 1.6E+01, 5.3E+01 | -                         | -     | 1.4E+01, 7.9E+01, 2.1E+05 | 4.6E+00, 1.1E+01, 4.8E+01 | 1.2E-04, 3.3E-01, 9.1E-01 |
| everything_but_singletons    | True        |          128 |              0 | -             | -                           |                 3.8 |                18   | 3.4E-07, 1.1E-05, 7.4E-03    | 1.0E+01, 1.6E+01, 5.3E+01 | 1.0E+00, 1.0E+00, 1.8E+01 | -     | 1.4E+01, 8.0E+01, 2.9E+05 | 4.6E+00, 1.2E+01, 4.8E+01 | 1.9E-04, 3.4E-01, 8.8E-01 |
| size_ge_11          | False       |          128 |              0 | 74.2          | 0.0E+00, 3.2E-02, 4.1E-01   |                 3.8 |                11.8 | 8.5E-07, 1.1E-05, 1.7E-02    | 1.0E+01, 1.6E+01, 5.3E+01 | -                         | -     | 1.4E+01, 7.9E+01, 2.1E+05 | 4.6E+00, 1.1E+01, 4.8E+01 | 1.2E-04, 3.3E-01, 9.1E-01 |
| size_ge_11          | True        |          128 |              0 | -             | -                           |                 3.8 |                18   | 3.4E-07, 1.1E-05, 7.4E-03    | 1.0E+01, 1.6E+01, 5.3E+01 | 1.0E+00, 1.0E+00, 1.8E+01 | -     | 1.4E+01, 8.0E+01, 2.9E+05 | 4.6E+00, 1.2E+01, 4.8E+01 | 1.9E-04, 3.4E-01, 8.8E-01 |
| not_tree            | False       |          128 |              0 | 74.2          | 0.0E+00, 3.2E-02, 4.1E-01   |                 3.8 |                11.8 | 8.5E-07, 1.1E-05, 1.7E-02    | 1.0E+01, 1.6E+01, 5.3E+01 | -                         | -     | 1.4E+01, 7.9E+01, 2.1E+05 | 4.6E+00, 1.1E+01, 4.8E+01 | 1.2E-04, 3.3E-01, 9.1E-01 |
| not_tree            | True        |          128 |              0 | -             | -                           |                 3.8 |                18   | 3.4E-07, 1.1E-05, 7.4E-03    | 1.0E+01, 1.6E+01, 5.3E+01 | 1.0E+00, 1.0E+00, 1.8E+01 | -     | 1.4E+01, 8.0E+01, 2.9E+05 | 4.6E+00, 1.2E+01, 4.8E+01 | 1.9E-04, 3.4E-01, 8.8E-01 |
| not_tree+size_ge_11 | False       |          128 |              0 | 74.2          | 0.0E+00, 3.2E-02, 4.1E-01   |                 3.8 |                11.8 | 8.5E-07, 1.1E-05, 1.7E-02    | 1.0E+01, 1.6E+01, 5.3E+01 | -                         | -     | 1.4E+01, 7.9E+01, 2.1E+05 | 4.6E+00, 1.1E+01, 4.8E+01 | 1.2E-04, 3.3E-01, 9.1E-01 |
| not_tree+size_ge_11 | True        |          128 |              0 | -             | -                           |                 3.8 |                18   | 3.4E-07, 1.1E-05, 7.4E-03    | 1.0E+01, 1.6E+01, 5.3E+01 | 1.0E+00, 1.0E+00, 1.8E+01 | -     | 1.4E+01, 8.0E+01, 2.9E+05 | 4.6E+00, 1.2E+01, 4.8E+01 | 1.9E-04, 3.4E-01, 8.8E-01 |
| only_tree           | False       |            0 |       13454271 | 0.0           | 0.0E+00, 0.0E+00, 0.0E+00   |                96.2 |                 0   | -1.0E-08, -1.2E-16, -3.0E-17 | 0.0E+00, 0.0E+00, 0.0E+00 | -                         | -     | 1.0E+00, 1.0E+00, 1.0E+00 | 0.0E+00, 0.0E+00, 0.0E+00 | 0.0E+00, 0.0E+00, 0.0E+00 |
| only_tree           | True        |            0 |       13454271 | -             | -                           |                96.2 |                 0   | -1.0E-08, -1.2E-16, -3.0E-17 | 0.0E+00, 0.0E+00, 0.0E+00 | 1.0E+00, 1.0E+00, 1.0E+00 | -     | 1.0E+00, 1.0E+00, 1.0E+00 | 0.0E+00, 0.0E+00, 0.0E+00 | 0.0E+00, 0.0E+00, 0.0E+00 |



## Observations

### Across different optimization problems / clustering criteria pre-AOC

 - Leiden+CPM produced many more clusters compared to modularity-based clustering and IKC
 - Leiden+Modularity surprisingly covered all nodes (100%!), IKC having the worst coverage. Leiden+CPM, even restricted to clusters having size >= 11 and not trees, still achieved substantially better coverage than IKC
 - Leiden+Modularity and Leiden+CPM have little guarantee for MCD and treeness, as expected

### Pre-AOC vs Post-AOC

 - With $r < 0.1$, Leiden+CPM augments very well. Notably, at $r = 0.0001$, the median size of the clusters *drastically* increased. With $r = 0.1$, Leiden+CPM did not augment at all.
 - Leiden+Modularity augments very well (median # of clusters per node very high). This seems actually problematic
 - IKC did not augment that well, but this is AOC_m, and from the original AOC paper we know that AOC_m is quite strict
 - For Leiden+CPM, modularity sometimes decreases post-AOC, sometimes increases post-AOC, dependent on $r$
 - AOC does not seem to decrease # of trees by a lot in general
 - AOC does not seem to decrease # of singletons by a lot in general

### Post-AOC comparisons

 - Leiden+modularity+AOC is extremely overlapping. The median clusters per node post-AOC is comparatively very large. Leiden+CPM+AOC is overlapping, but the median clusters per node is still small (very often $1$)
 - Except for Leiden+CPM $r = 0.1$, most clusters did augment once considering those that are eligible (size >= 11).