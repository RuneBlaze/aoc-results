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
   - `all`: all clusters
   - `size_ge_11`: all clusters with size at least 11
   - `not_tree`: those that are not trees
   - `only_tree`: those that are trees
   - `A+B`: both `A` and `B` applied
 - `augmented`: post-AOC (true) or pre-AOC
 - `# singletons`: for `variant = all`, the true number of singletons. All other rows have no obvious meaning
 - `Deviation from treeness`: `(m - n + 1 ) / n`

Distributions are written in minimum, median, maximum format.

## A resolution limit statement for AOC paired with CPM

Assume $G = (V, E)$ as the background network. Assume $G$ is connected. Consider a cluster $K_i$ to be augmented
by AOC using the CPM criterion, with resolution value $\gamma$ for AOC (the original clustering can be arbitrary).
Let $n$ be the number of nodes in $K_i$ and $m$ the number of edges in $K_i$. Assume $n \ll |V|$.

> **Theorem**: if $\gamma = 0.01$, $K_i$ after AOC augmentation will have size $\geq 101$. That is, clusters below size $101$
> will never be detected by AOC. (Similarly, if $\gamma = 0.0001$, $K_i$ after AOC augmentation will have size $\geq 10001$ **(!)**)

Proof omitted due to time constraints. Note that when $\gamma = 0.0001$, $K_i$ drawn from the CPM+Leiden cluster
distributions on CEN before AOC has median size 380. That is,
at least half of the clusters will be bloated to size $\geq 10001$.


## Tables for `cen.tsv.leiden_cpm_0.1`

| Variant             | Augmented   |   # Clusters |   # Singletons | % Augmented   | Relative Increase in Size   |   Node Coverage (%) |   Edge Coverage (%) | Modularity                 | MCD                       | Clusters Per Node         | CPM                       | Size                      | Deviation from Treeness   | Density                   |
|---------------------|-------------|--------------|----------------|---------------|-----------------------------|---------------------|---------------------|----------------------------|---------------------------|---------------------------|---------------------------|---------------------------|---------------------------|---------------------------|
| all                 | False       |       516922 |        8336638 | 0.0           | 0.0E+00, 0.0E+00, 0.0E+00   |                40.4 |                 9.6 | -5.6E-08, 1.1E-07, 1.3E-04 | 1.0E+00, 1.0E+00, 3.3E+01 | -                         | 9.0E-01, 4.5E+00, 6.5E+03 | 2.0E+00, 1.1E+01, 3.2E+02 | 0.0E+00, 0.0E+00, 3.5E+01 | 1.4E-01, 1.9E-01, 1.0E+00 |
| all                 | True        |       516922 |        8336638 | -             | -                           |                40.4 |                 9.6 | -5.6E-08, 1.1E-07, 1.3E-04 | 1.0E+00, 1.0E+00, 3.3E+01 | 1.0E+00, 1.0E+00, 1.0E+00 | 9.0E-01, 4.5E+00, 6.5E+03 | 2.0E+00, 1.1E+01, 3.2E+02 | 0.0E+00, 0.0E+00, 3.5E+01 | 1.4E-01, 1.9E-01, 1.0E+00 |
| size_ge_11          | False       |       275193 |       10618604 | 0.0           | 0.0E+00, 0.0E+00, 0.0E+00   |                24.1 |                 7.4 | -5.6E-08, 1.1E-07, 1.3E-04 | 1.0E+00, 1.0E+00, 3.3E+01 | -                         | 4.5E+00, 4.5E+00, 6.5E+03 | 1.1E+01, 1.1E+01, 3.2E+02 | 0.0E+00, 0.0E+00, 3.5E+01 | 1.4E-01, 1.8E-01, 5.9E-01 |
| size_ge_11          | True        |       275193 |       10618604 | -             | -                           |                24.1 |                 7.4 | -5.6E-08, 1.1E-07, 1.3E-04 | 1.0E+00, 1.0E+00, 3.3E+01 | 1.0E+00, 1.0E+00, 1.0E+00 | 4.5E+00, 4.5E+00, 6.5E+03 | 1.1E+01, 1.1E+01, 3.2E+02 | 0.0E+00, 0.0E+00, 3.5E+01 | 1.4E-01, 1.8E-01, 5.9E-01 |
| not_tree            | False       |        21483 |       13414565 | 0.0           | 0.0E+00, 0.0E+00, 0.0E+00   |                 4.1 |                 4.6 | 3.3E-08, 3.6E-07, 1.3E-04  | 1.0E+00, 2.0E+00, 3.3E+01 | -                         | 2.7E+00, 1.7E+01, 6.5E+03 | 3.0E+00, 1.8E+01, 3.2E+02 | 9.1E-02, 8.5E-01, 3.5E+01 | 1.4E-01, 2.5E-01, 1.0E+00 |
| not_tree            | True        |        21483 |       13414565 | -             | -                           |                 4.1 |                 4.6 | 3.3E-08, 3.6E-07, 1.3E-04  | 1.0E+00, 2.0E+00, 3.3E+01 | 1.0E+00, 1.0E+00, 1.0E+00 | 2.7E+00, 1.7E+01, 6.5E+03 | 3.0E+00, 1.8E+01, 3.2E+02 | 9.1E-02, 8.5E-01, 3.5E+01 | 1.4E-01, 2.5E-01, 1.0E+00 |
| not_tree+size_ge_11 | False       |        18579 |       13441358 | 0.0           | 0.0E+00, 0.0E+00, 0.0E+00   |                 3.9 |                 4.6 | 1.2E-07, 3.9E-07, 1.3E-04  | 1.0E+00, 2.0E+00, 3.3E+01 | -                         | 5.5E+00, 1.7E+01, 6.5E+03 | 1.1E+01, 1.9E+01, 3.2E+02 | 9.1E-02, 8.6E-01, 3.5E+01 | 1.4E-01, 2.5E-01, 5.9E-01 |
| not_tree+size_ge_11 | True        |        18579 |       13441358 | -             | -                           |                 3.9 |                 4.6 | 1.2E-07, 3.9E-07, 1.3E-04  | 1.0E+00, 2.0E+00, 3.3E+01 | 1.0E+00, 1.0E+00, 1.0E+00 | 5.5E+00, 1.7E+01, 6.5E+03 | 1.1E+01, 1.9E+01, 3.2E+02 | 9.1E-02, 8.6E-01, 3.5E+01 | 1.4E-01, 2.5E-01, 5.9E-01 |
| only_tree           | False       |       495439 |        8911509 | 0.0           | 0.0E+00, 0.0E+00, 0.0E+00   |                36.3 |                 5   | -5.6E-08, 1.1E-07, 1.1E-07 | 1.0E+00, 1.0E+00, 1.0E+00 | -                         | 9.0E-01, 4.5E+00, 4.5E+00 | 2.0E+00, 1.1E+01, 1.1E+01 | 0.0E+00, 0.0E+00, 0.0E+00 | 1.8E-01, 1.8E-01, 1.0E+00 |
| only_tree           | True        |       495439 |        8911509 | -             | -                           |                36.3 |                 5   | -5.6E-08, 1.1E-07, 1.1E-07 | 1.0E+00, 1.0E+00, 1.0E+00 | 1.0E+00, 1.0E+00, 1.0E+00 | 9.0E-01, 4.5E+00, 4.5E+00 | 2.0E+00, 1.1E+01, 1.1E+01 | 0.0E+00, 0.0E+00, 0.0E+00 | 1.8E-01, 1.8E-01, 1.0E+00 |
## Tables for `cen.tsv.leiden_cpm_0.01`

| Variant             | Augmented   |   # Clusters |   # Singletons | % Augmented   | Relative Increase in Size   |   Node Coverage (%) |   Edge Coverage (%) | Modularity                  | MCD                       | Clusters Per Node         | CPM                       | Size                      | Deviation from Treeness   | Density                   |
|---------------------|-------------|--------------|----------------|---------------|-----------------------------|---------------------|---------------------|-----------------------------|---------------------------|---------------------------|---------------------------|---------------------------|---------------------------|---------------------------|
| all                 | False       |       280229 |        3243923 | 93.9          | 0.0E+00, 4.9E+00, 1.6E+01   |                76.8 |                24.4 | -8.6E-07, 3.0E-07, 1.6E-03  | 1.0E+00, 1.0E+00, 3.5E+01 | -                         | 9.9E-01, 2.4E+01, 9.0E+04 | 2.0E+00, 2.8E+01, 3.3E+03 | 0.0E+00, 0.0E+00, 4.3E+01 | 1.9E-02, 7.5E-02, 1.0E+00 |
| all                 | True        |       280229 |        3243081 | -             | -                           |                76.8 |                25   | -6.3E-05, -2.8E-05, 1.6E-03 | 1.0E+00, 1.0E+00, 3.5E+01 | 1.0E+00, 1.0E+00, 2.5E+05 | 9.9E-01, 2.4E+01, 9.0E+04 | 2.0E+00, 1.7E+02, 3.3E+03 | 0.0E+00, 0.0E+00, 4.3E+01 | 1.1E-02, 1.2E-02, 1.0E+00 |
| size_ge_11          | False       |       275415 |        3282592 | 95.5          | 0.0E+00, 5.2E+00, 1.6E+01   |                76.5 |                24.4 | -8.6E-07, 3.2E-07, 1.6E-03  | 1.0E+00, 1.0E+00, 3.5E+01 | -                         | 9.4E+00, 2.5E+01, 9.0E+04 | 1.1E+01, 2.8E+01, 3.3E+03 | 0.0E+00, 0.0E+00, 4.3E+01 | 1.9E-02, 7.4E-02, 3.1E-01 |
| size_ge_11          | True        |       275415 |        3281671 | -             | -                           |                76.5 |                24.9 | -6.3E-05, -2.9E-05, 1.6E-03 | 1.0E+00, 1.0E+00, 3.5E+01 | 1.0E+00, 1.0E+00, 2.5E+05 | 9.4E+00, 2.5E+01, 9.0E+04 | 1.1E+01, 1.7E+02, 3.3E+03 | 0.0E+00, 0.0E+00, 4.3E+01 | 1.1E-02, 1.2E-02, 2.1E-01 |
| not_tree            | False       |        64611 |       10505606 | 92.6          | 0.0E+00, 3.9E+00, 1.6E+01   |                24.9 |                16.8 | 3.3E-08, 4.7E-07, 1.6E-03   | 1.0E+00, 1.0E+00, 3.5E+01 | -                         | 3.0E+00, 3.7E+01, 9.0E+04 | 3.0E+00, 3.4E+01, 3.3E+03 | 9.9E-03, 2.8E-01, 4.3E+01 | 1.9E-02, 7.7E-02, 1.0E+00 |
| not_tree            | True        |        64617 |       10500387 | -             | -                           |                24.9 |                16.9 | -6.0E-05, -2.6E-05, 1.6E-03 | 1.0E+00, 1.0E+00, 3.5E+01 | 1.0E+00, 1.0E+00, 5.8E+04 | 3.0E+00, 3.8E+01, 9.0E+04 | 3.0E+00, 1.7E+02, 3.3E+03 | 5.3E-03, 5.7E-02, 4.3E+01 | 1.1E-02, 1.3E-02, 1.0E+00 |
| not_tree+size_ge_11 | False       |        64538 |       10506230 | 92.7          | 0.0E+00, 3.9E+00, 1.6E+01   |                24.9 |                16.8 | 1.2E-07, 4.7E-07, 1.6E-03   | 1.0E+00, 1.0E+00, 3.5E+01 | -                         | 1.0E+01, 3.7E+01, 9.0E+04 | 1.1E+01, 3.4E+01, 3.3E+03 | 9.9E-03, 2.8E-01, 4.3E+01 | 1.9E-02, 7.7E-02, 3.1E-01 |
| not_tree+size_ge_11 | True        |        64544 |       10501011 | -             | -                           |                24.9 |                16.9 | -6.0E-05, -2.6E-05, 1.6E-03 | 1.0E+00, 1.0E+00, 3.5E+01 | 1.0E+00, 1.0E+00, 5.8E+04 | 9.6E+00, 3.8E+01, 9.0E+04 | 1.2E+01, 1.7E+02, 3.3E+03 | 5.3E-03, 5.7E-02, 4.3E+01 | 1.1E-02, 1.3E-02, 2.1E-01 |
| only_tree           | False       |       215618 |        6727753 | 94.3          | 0.0E+00, 5.4E+00, 1.6E+01   |                51.9 |                 7.7 | -8.6E-07, 2.8E-07, 1.1E-06  | 1.0E+00, 1.0E+00, 1.0E+00 | -                         | 9.9E-01, 2.2E+01, 5.0E+01 | 2.0E+00, 2.7E+01, 1.0E+02 | 0.0E+00, 0.0E+00, 0.0E+00 | 2.0E-02, 7.4E-02, 1.0E+00 |
| only_tree           | True        |       215612 |        6712542 | -             | -                           |                52   |                 8.1 | -6.3E-05, -2.9E-05, 1.8E-06 | 1.0E+00, 1.0E+00, 1.0E+00 | 1.0E+00, 1.0E+00, 2.0E+05 | 9.9E-01, 2.2E+01, 5.0E+01 | 2.0E+00, 1.7E+02, 1.9E+02 | 0.0E+00, 0.0E+00, 0.0E+00 | 1.1E-02, 1.1E-02, 1.0E+00 |
## Tables for `cen.tsv.leiden_cpm_0.001`

| Variant             | Augmented   |   # Clusters |   # Singletons | % Augmented   | Relative Increase in Size   |   Node Coverage (%) |   Edge Coverage (%) | Modularity                  | MCD                       | Clusters Per Node         | CPM                       | Size                      | Deviation from Treeness   | Density                   |
|---------------------|-------------|--------------|----------------|---------------|-----------------------------|---------------------|---------------------|-----------------------------|---------------------------|---------------------------|---------------------------|---------------------------|---------------------------|---------------------------|
| all                 | False       |        66410 |        2180745 | 96.9          | 0.0E+00, 1.8E+01, 1.8E+02   |                84.4 |                39.1 | 1.1E-08, 1.1E-06, 6.3E-03   | 1.0E+00, 1.0E+00, 1.8E+01 | -                         | 1.0E+00, 9.9E+01, 4.4E+05 | 2.0E+00, 9.6E+01, 1.8E+04 | 0.0E+00, 4.2E-02, 3.2E+01 | 2.0E-03, 2.3E-02, 1.0E+00 |
| all                 | True        |        66410 |        2180328 | -             | -                           |                84.4 |                39.4 | -2.2E-04, -1.4E-04, 6.3E-03 | 1.0E+00, 1.0E+00, 1.8E+01 | 1.0E+00, 1.0E+00, 6.4E+04 | 1.0E+00, 1.0E+02, 4.4E+05 | 2.0E+00, 1.9E+03, 1.8E+04 | 0.0E+00, 1.7E-03, 3.2E+01 | 1.0E-03, 1.1E-03, 1.0E+00 |
| size_ge_11          | False       |        65836 |        2183204 | 97.7          | 0.0E+00, 1.9E+01, 1.8E+02   |                84.4 |                39.1 | 1.1E-07, 1.1E-06, 6.3E-03   | 1.0E+00, 1.0E+00, 1.8E+01 | -                         | 9.9E+00, 1.0E+02, 4.4E+05 | 1.1E+01, 9.7E+01, 1.8E+04 | 0.0E+00, 4.3E-02, 3.2E+01 | 2.0E-03, 2.3E-02, 2.3E-01 |
| size_ge_11          | True        |        65836 |        2182787 | -             | -                           |                84.4 |                39.4 | -2.2E-04, -1.4E-04, 6.3E-03 | 1.0E+00, 1.0E+00, 1.8E+01 | 1.0E+00, 1.0E+00, 6.4E+04 | 9.9E+00, 1.0E+02, 4.4E+05 | 1.1E+01, 1.9E+03, 1.8E+04 | 0.0E+00, 2.1E-03, 3.2E+01 | 1.0E-03, 1.1E-03, 2.1E-01 |
| not_tree            | False       |        42845 |        5299173 | 97.7          | 0.0E+00, 1.6E+01, 1.4E+02   |                62.1 |                35.8 | 4.3E-08, 1.4E-06, 6.3E-03   | 1.0E+00, 1.0E+00, 1.8E+01 | -                         | 4.0E+00, 1.2E+02, 4.4E+05 | 4.0E+00, 1.1E+02, 1.8E+04 | 2.0E-03, 1.3E-01, 3.2E+01 | 2.4E-03, 2.1E-02, 6.7E-01 |
| not_tree            | True        |        42848 |        5297498 | -             | -                           |                62.1 |                36   | -2.2E-04, -1.4E-04, 6.3E-03 | 1.0E+00, 1.0E+00, 1.8E+01 | 1.0E+00, 1.0E+00, 4.2E+04 | 4.0E+00, 1.2E+02, 4.4E+05 | 4.0E+00, 1.9E+03, 1.8E+04 | 5.0E-04, 7.2E-03, 3.2E+01 | 1.0E-03, 1.1E-03, 6.7E-01 |
| not_tree+size_ge_11 | False       |        42840 |        5299202 | 97.7          | 0.0E+00, 1.6E+01, 1.4E+02   |                62.1 |                35.8 | 1.5E-07, 1.4E-06, 6.3E-03   | 1.0E+00, 1.0E+00, 1.8E+01 | -                         | 1.4E+01, 1.2E+02, 4.4E+05 | 1.2E+01, 1.1E+02, 1.8E+04 | 2.0E-03, 1.3E-01, 3.2E+01 | 2.4E-03, 2.1E-02, 2.3E-01 |
| not_tree+size_ge_11 | True        |        42843 |        5297527 | -             | -                           |                62.1 |                36   | -2.2E-04, -1.4E-04, 6.3E-03 | 1.0E+00, 1.0E+00, 1.8E+01 | 1.0E+00, 1.0E+00, 4.2E+04 | 1.0E+01, 1.2E+02, 4.4E+05 | 1.2E+01, 1.9E+03, 1.8E+04 | 5.0E-04, 7.2E-03, 3.2E+01 | 1.0E-03, 1.1E-03, 2.1E-01 |
| only_tree           | False       |        23565 |       10871008 | 95.4          | 0.0E+00, 2.8E+01, 1.8E+02   |                22.3 |                 3.4 | 1.1E-08, 6.8E-07, 1.1E-05   | 1.0E+00, 1.0E+00, 1.0E+00 | -                         | 1.0E+00, 6.1E+01, 5.0E+02 | 2.0E+00, 6.4E+01, 1.0E+03 | 0.0E+00, 0.0E+00, 0.0E+00 | 2.0E-03, 3.1E-02, 1.0E+00 |
| only_tree           | True        |        23562 |       10860339 | -             | -                           |                22.4 |                 3.5 | -2.1E-04, -1.6E-04, 1.1E-05 | 1.0E+00, 1.0E+00, 1.0E+00 | 1.0E+00, 1.0E+00, 2.2E+04 | 1.0E+00, 6.2E+01, 5.0E+02 | 2.0E+00, 1.9E+03, 2.0E+03 | 0.0E+00, 0.0E+00, 0.0E+00 | 1.0E-03, 1.0E-03, 1.0E+00 |
## Tables for `cen.tsv.leiden_cpm_0.0001`

| Variant             | Augmented   |   # Clusters |   # Singletons | % Augmented   | Relative Increase in Size   |   Node Coverage (%) |   Edge Coverage (%) | Modularity                  | MCD                       | Clusters Per Node         | CPM                       | Size                      | Deviation from Treeness   | Density                   |
|---------------------|-------------|--------------|----------------|---------------|-----------------------------|---------------------|---------------------|-----------------------------|---------------------------|---------------------------|---------------------------|---------------------------|---------------------------|---------------------------|
| all                 | False       |        11829 |        1303375 | 94.3          | 0.0E+00, 4.5E+01, 1.8E+03   |                90.7 |                51.7 | 1.1E-08, 4.6E-06, 1.7E-02   | 1.0E+00, 1.0E+00, 7.0E+00 | -                         | 1.0E+00, 4.2E+02, 1.4E+06 | 2.0E+00, 3.8E+02, 7.0E+04 | 0.0E+00, 9.4E-02, 2.3E+01 | 2.0E-04, 6.0E-03, 1.0E+00 |
| all                 | True        |        11829 |        1301956 | -             | -                           |                90.7 |                51.9 | -3.7E-04, -2.1E-04, 1.7E-02 | 1.0E+00, 1.0E+00, 7.0E+00 | 1.0E+00, 1.0E+00, 1.1E+04 | 1.0E+00, 4.2E+02, 1.4E+06 | 2.0E+00, 2.0E+04, 7.0E+04 | 0.0E+00, 1.6E-03, 2.3E+01 | 1.0E-04, 1.0E-04, 1.0E+00 |
| size_ge_11          | False       |        11381 |        1305292 | 98.0          | 0.0E+00, 4.8E+01, 1.8E+03   |                90.7 |                51.7 | 1.1E-07, 5.0E-06, 1.7E-02   | 1.0E+00, 1.0E+00, 7.0E+00 | -                         | 1.0E+01, 4.5E+02, 1.4E+06 | 1.1E+01, 4.0E+02, 7.0E+04 | 0.0E+00, 1.0E-01, 2.3E+01 | 2.0E-04, 5.8E-03, 2.3E-01 |
| size_ge_11          | True        |        11381 |        1303872 | -             | -                           |                90.7 |                51.9 | -3.7E-04, -2.1E-04, 1.7E-02 | 1.0E+00, 1.0E+00, 7.0E+00 | 1.0E+00, 1.0E+00, 1.1E+04 | 1.0E+01, 4.5E+02, 1.4E+06 | 1.1E+01, 2.0E+04, 7.0E+04 | 0.0E+00, 1.8E-03, 2.3E+01 | 1.0E-04, 1.0E-04, 2.1E-01 |
| not_tree            | False       |         9534 |        2631485 | 98.1          | 0.0E+00, 4.1E+01, 1.8E+03   |                81.2 |                50.2 | 3.3E-08, 5.9E-06, 1.7E-02   | 1.0E+00, 1.0E+00, 7.0E+00 | -                         | 3.0E+00, 5.3E+02, 1.4E+06 | 3.0E+00, 4.6E+02, 7.0E+04 | 3.8E-04, 1.4E-01, 2.3E+01 | 2.8E-04, 5.1E-03, 1.0E+00 |
| not_tree            | True        |         9537 |        2627640 | -             | -                           |                81.2 |                50.5 | -3.7E-04, -2.0E-04, 1.7E-02 | 1.0E+00, 1.0E+00, 7.0E+00 | 1.0E+00, 1.0E+00, 9.3E+03 | 3.0E+00, 5.3E+02, 1.4E+06 | 3.0E+00, 2.0E+04, 7.0E+04 | 5.0E-05, 3.1E-03, 2.3E+01 | 1.0E-04, 1.0E-04, 1.0E+00 |
| not_tree+size_ge_11 | False       |         9528 |        2631520 | 98.2          | 0.0E+00, 4.1E+01, 1.8E+03   |                81.2 |                50.2 | 1.2E-07, 5.9E-06, 1.7E-02   | 1.0E+00, 1.0E+00, 7.0E+00 | -                         | 1.1E+01, 5.3E+02, 1.4E+06 | 1.1E+01, 4.6E+02, 7.0E+04 | 3.8E-04, 1.4E-01, 2.3E+01 | 2.8E-04, 5.1E-03, 2.3E-01 |
| not_tree+size_ge_11 | True        |         9531 |        2627675 | -             | -                           |                81.2 |                50.5 | -3.7E-04, -2.0E-04, 1.7E-02 | 1.0E+00, 1.0E+00, 7.0E+00 | 1.0E+00, 1.0E+00, 9.3E+03 | 1.0E+01, 5.3E+02, 1.4E+06 | 1.2E+01, 2.0E+04, 7.0E+04 | 5.0E-05, 3.1E-03, 2.3E+01 | 1.0E-04, 1.0E-04, 2.1E-01 |
| only_tree           | False       |         2295 |       12661326 | 78.3          | 0.0E+00, 1.2E+02, 1.8E+03   |                 9.5 |                 1.4 | 1.1E-08, 9.7E-07, 1.1E-04   | 1.0E+00, 1.0E+00, 1.0E+00 | -                         | 1.0E+00, 8.9E+01, 5.0E+03 | 2.0E+00, 9.0E+01, 1.0E+04 | 0.0E+00, 0.0E+00, 0.0E+00 | 2.0E-04, 2.2E-02, 1.0E+00 |
| only_tree           | True        |         2292 |       12629672 | -             | -                           |                 9.7 |                 1.5 | -3.7E-04, -2.7E-04, 1.1E-04 | 1.0E+00, 1.0E+00, 1.0E+00 | 1.0E+00, 1.0E+00, 1.8E+03 | 1.0E+00, 8.9E+01, 5.0E+03 | 2.0E+00, 2.0E+04, 2.0E+04 | 0.0E+00, 0.0E+00, 0.0E+00 | 1.0E-04, 1.0E-04, 1.0E+00 |
## Tables for `cen.tsv.leiden_mod`

| Variant             | Augmented   |   # Clusters |   # Singletons | % Augmented   | Relative Increase in Size   |   Node Coverage (%) |   Edge Coverage (%) | Modularity                | MCD                       | Clusters Per Node         | CPM   | Size                      | Deviation from Treeness   | Density                   |
|---------------------|-------------|--------------|----------------|---------------|-----------------------------|---------------------|---------------------|---------------------------|---------------------------|---------------------------|-------|---------------------------|---------------------------|---------------------------|
| all                 | False       |          257 |              0 | 62.3          | 0.0E+00, 1.3E+03, 1.2E+06   |               100   |                72.3 | 1.1E-08, 3.6E-07, 6.7E-02 | 1.0E+00, 1.0E+00, 1.0E+00 | -                         | -     | 2.0E+00, 3.4E+01, 1.3E+06 | 0.0E+00, 0.0E+00, 7.3E+00 | 4.2E-06, 5.9E-02, 1.0E+00 |
| all                 | True        |          257 |              0 | -             | -                           |               100   |               100   | 1.1E-08, 1.5E-05, 6.7E-02 | 1.0E+00, 1.0E+00, 1.0E+00 | 1.0E+00, 1.6E+02, 1.6E+02 | -     | 2.0E+00, 1.4E+07, 1.4E+07 | 0.0E+00, 5.6E+00, 6.3E+00 | 9.4E-07, 9.4E-07, 1.0E+00 |
| size_ge_11          | False       |          193 |            287 | 82.9          | 0.0E+00, 1.1E+05, 1.2E+06   |               100   |                72.3 | 1.1E-07, 6.1E-07, 6.7E-02 | 1.0E+00, 1.0E+00, 1.0E+00 | -                         | -     | 1.1E+01, 5.7E+01, 1.3E+06 | 0.0E+00, 0.0E+00, 7.3E+00 | 4.2E-06, 3.5E-02, 2.1E-01 |
| size_ge_11          | True        |          193 |            222 | -             | -                           |               100   |               100   | 1.1E-07, 1.6E-05, 6.7E-02 | 1.0E+00, 1.0E+00, 1.0E+00 | 1.0E+00, 1.6E+02, 1.6E+02 | -     | 1.1E+01, 1.4E+07, 1.4E+07 | 0.0E+00, 5.6E+00, 6.3E+00 | 9.4E-07, 9.4E-07, 2.1E-01 |
| not_tree            | False       |           56 |           9032 | 98.2          | 0.0E+00, 1.6E+02, 2.1E+05   |                99.9 |                72.3 | 1.5E-07, 9.0E-04, 6.7E-02 | 1.0E+00, 1.0E+00, 1.0E+00 | -                         | -     | 1.2E+01, 6.1E+04, 1.3E+06 | 1.9E-03, 6.3E-01, 7.3E+00 | 4.2E-06, 9.0E-05, 2.1E-01 |
| not_tree            | True        |          161 |            998 | -             | -                           |               100   |               100   | 1.5E-07, 1.6E-05, 6.7E-02 | 1.0E+00, 1.0E+00, 1.0E+00 | 1.0E+00, 1.6E+02, 1.6E+02 | -     | 1.2E+01, 1.4E+07, 1.4E+07 | 2.5E-01, 5.6E+00, 6.3E+00 | 9.4E-07, 9.4E-07, 2.1E-01 |
| not_tree+size_ge_11 | False       |           56 |           9032 | 98.2          | 0.0E+00, 1.6E+02, 2.1E+05   |                99.9 |                72.3 | 1.5E-07, 9.0E-04, 6.7E-02 | 1.0E+00, 1.0E+00, 1.0E+00 | -                         | -     | 1.2E+01, 6.1E+04, 1.3E+06 | 1.9E-03, 6.3E-01, 7.3E+00 | 4.2E-06, 9.0E-05, 2.1E-01 |
| not_tree+size_ge_11 | True        |          161 |            998 | -             | -                           |               100   |               100   | 1.5E-07, 1.6E-05, 6.7E-02 | 1.0E+00, 1.0E+00, 1.0E+00 | 1.0E+00, 1.6E+02, 1.6E+02 | -     | 1.2E+01, 1.4E+07, 1.4E+07 | 2.5E-01, 5.6E+00, 6.3E+00 | 9.4E-07, 9.4E-07, 2.1E-01 |
| only_tree           | False       |          201 |       13980404 | 52.2          | 0.0E+00, 8.2E+04, 1.2E+06   |                 0.1 |                 0   | 1.1E-08, 2.1E-07, 1.1E-05 | 1.0E+00, 1.0E+00, 1.0E+00 | -                         | -     | 2.0E+00, 2.0E+01, 1.1E+03 | 0.0E+00, 0.0E+00, 0.0E+00 | 1.9E-03, 1.0E-01, 1.0E+00 |
| only_tree           | True        |           96 |       13988373 | -             | -                           |                 0   |                 0   | 1.1E-08, 6.0E-08, 6.1E-07 | 1.0E+00, 1.0E+00, 1.0E+00 | 1.0E+00, 1.0E+00, 1.0E+00 | -     | 2.0E+00, 6.5E+00, 5.7E+01 | 0.0E+00, 0.0E+00, 0.0E+00 | 3.5E-02, 3.1E-01, 1.0E+00 |
## Tables for `cen.tsv.ikc10`

| Variant             | Augmented   |   # Clusters |   # Singletons | % Augmented   | Relative Increase in Size   |   Node Coverage (%) |   Edge Coverage (%) | Modularity                | MCD                       | Clusters Per Node         | CPM   | Size                      | Deviation from Treeness   | Density                   |
|---------------------|-------------|--------------|----------------|---------------|-----------------------------|---------------------|---------------------|---------------------------|---------------------------|---------------------------|-------|---------------------------|---------------------------|---------------------------|
| all                 | False       |          128 |       13454271 | 74.2          | 0.0E+00, 3.2E-02, 4.1E-01   |                 3.8 |                11.8 | 8.5E-07, 1.1E-05, 1.7E-02 | 1.0E+01, 1.6E+01, 5.3E+01 | -                         | -     | 1.4E+01, 7.9E+01, 2.1E+05 | 4.6E+00, 1.1E+01, 4.8E+01 | 1.2E-04, 3.3E-01, 9.1E-01 |
| all                 | True        |          128 |       13454271 | -             | -                           |                 3.8 |                18   | 3.4E-07, 1.1E-05, 7.4E-03 | 1.0E+01, 1.6E+01, 5.3E+01 | 1.0E+00, 1.0E+00, 1.8E+01 | -     | 1.4E+01, 8.0E+01, 2.9E+05 | 4.6E+00, 1.2E+01, 4.8E+01 | 1.9E-04, 3.4E-01, 8.8E-01 |
| size_ge_11          | False       |          128 |       13454271 | 74.2          | 0.0E+00, 3.2E-02, 4.1E-01   |                 3.8 |                11.8 | 8.5E-07, 1.1E-05, 1.7E-02 | 1.0E+01, 1.6E+01, 5.3E+01 | -                         | -     | 1.4E+01, 7.9E+01, 2.1E+05 | 4.6E+00, 1.1E+01, 4.8E+01 | 1.2E-04, 3.3E-01, 9.1E-01 |
| size_ge_11          | True        |          128 |       13454271 | -             | -                           |                 3.8 |                18   | 3.4E-07, 1.1E-05, 7.4E-03 | 1.0E+01, 1.6E+01, 5.3E+01 | 1.0E+00, 1.0E+00, 1.8E+01 | -     | 1.4E+01, 8.0E+01, 2.9E+05 | 4.6E+00, 1.2E+01, 4.8E+01 | 1.9E-04, 3.4E-01, 8.8E-01 |
| not_tree            | False       |          128 |       13454271 | 74.2          | 0.0E+00, 3.2E-02, 4.1E-01   |                 3.8 |                11.8 | 8.5E-07, 1.1E-05, 1.7E-02 | 1.0E+01, 1.6E+01, 5.3E+01 | -                         | -     | 1.4E+01, 7.9E+01, 2.1E+05 | 4.6E+00, 1.1E+01, 4.8E+01 | 1.2E-04, 3.3E-01, 9.1E-01 |
| not_tree            | True        |          128 |       13454271 | -             | -                           |                 3.8 |                18   | 3.4E-07, 1.1E-05, 7.4E-03 | 1.0E+01, 1.6E+01, 5.3E+01 | 1.0E+00, 1.0E+00, 1.8E+01 | -     | 1.4E+01, 8.0E+01, 2.9E+05 | 4.6E+00, 1.2E+01, 4.8E+01 | 1.9E-04, 3.4E-01, 8.8E-01 |
| not_tree+size_ge_11 | False       |          128 |       13454271 | 74.2          | 0.0E+00, 3.2E-02, 4.1E-01   |                 3.8 |                11.8 | 8.5E-07, 1.1E-05, 1.7E-02 | 1.0E+01, 1.6E+01, 5.3E+01 | -                         | -     | 1.4E+01, 7.9E+01, 2.1E+05 | 4.6E+00, 1.1E+01, 4.8E+01 | 1.2E-04, 3.3E-01, 9.1E-01 |
| not_tree+size_ge_11 | True        |          128 |       13454271 | -             | -                           |                 3.8 |                18   | 3.4E-07, 1.1E-05, 7.4E-03 | 1.0E+01, 1.6E+01, 5.3E+01 | 1.0E+00, 1.0E+00, 1.8E+01 | -     | 1.4E+01, 8.0E+01, 2.9E+05 | 4.6E+00, 1.2E+01, 4.8E+01 | 1.9E-04, 3.4E-01, 8.8E-01 |
| only_tree           | False       |            0 |       13989436 | 0.0           | 0.0E+00, 0.0E+00, 0.0E+00   |                 0   |                 0   | 0.0E+00, 0.0E+00, 0.0E+00 | 0.0E+00, 0.0E+00, 0.0E+00 | -                         | -     | 0.0E+00, 0.0E+00, 0.0E+00 | 0.0E+00, 0.0E+00, 0.0E+00 | 0.0E+00, 0.0E+00, 0.0E+00 |
| only_tree           | True        |            0 |       13989436 | -             | -                           |                 0   |                 0   | 0.0E+00, 0.0E+00, 0.0E+00 | 0.0E+00, 0.0E+00, 0.0E+00 | 0.0E+00, 0.0E+00, 0.0E+00 | -     | 0.0E+00, 0.0E+00, 0.0E+00 | 0.0E+00, 0.0E+00, 0.0E+00 | 0.0E+00, 0.0E+00, 0.0E+00 |