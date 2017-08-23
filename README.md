# Paper
Code to reproduce results in "Finding Streams in Knowledge Graphs to Support Fact Checking" in proceedings of ICDM 2017.

# Fetch and install
```
git clone https://github.com/shiralkarprashant/knowledgestream
cd knowledgestream
```

# Data
Download data from the following URL http://carl.cs.indiana.edu/data/fact-checking/data.zip and decompress it inside `knowledgestream` directory.

# Install
```python setup.py install```

# Run 

## Knowledge Stream (KS)

```kstream -m stream -d ./datasets/sample.csv -o output/```

You should see output such as 

```
[19:00:10] Launching stream..
[19:00:10] Dataset: sample.csv
[19:00:10] Output dir: /Users/pshiralk/Projects/knowledgestream/output
[19:00:10] Read data: (5, 7) sample.csv
[19:00:10] Note: Found non-NA records: (5, 7)
Reconstructing graph from /Users/pshiralk/Projects/knowledgestream/data/kg/_undir
=> Loaded: undir_data.npy
=> Loaded: undir_indptr.npy
=> Loaded: undir_indices.npy
=> Loaded: undir_indeg_vec.npy
=> Graph loaded: 11.63 secs.

[19:00:22] Computing KNOWLEDGE-STREAM for 5 triples..
1. Working on (2985653, 599, 3218267) .. [19:00:38] mincostflow: 0.08863, #paths: 5, time: 12.55s.
 2. Working on (2734002, 599, 5305646) .. [19:00:52] mincostflow: 0.15648, #paths: 5, time: 12.91s.
 3. Working on (5140024, 599, 4567127) .. [19:01:01] mincostflow: 0.16628, #paths: 5, time: 9.20s.
 4. Working on (1522148, 599, 1357357) .. [19:01:11] mincostflow: 0.09414, #paths: 5, time: 9.28s.
 5. Working on (4319468, 599, 2450828) .. [19:01:19] mincostflow: 0.16025, #paths: 5, time: 8.05s.
[19:01:19] * Saved results: /Users/pshiralk/Projects/knowledgestream/output/out_kstream_sample_2017-08-23.csv
[19:01:19] Mincostflow computation complete. Time taken: 57.64 secs.
```
and a CSV file is created at the specified output directory, which contains `score` and `softmaxscore` (normalized) for each triple.

## Relational Knowledge Linker (KL-REL)

```kstream -m relklinker -d ./datasets/sample.csv -o output/```

You should see output such as 

```
[18:56:43] Launching relklinker..
[18:56:43] Dataset: sample.csv
[18:56:43] Output dir: knowledgestream/output
[18:56:43] Read data: (5, 7) sample.csv
[18:56:43] Note: Found non-NA records: (5, 7)
Reconstructing graph from knowledgestream/data/kg/_undir
=> Loaded: undir_data.npy
=> Loaded: undir_indptr.npy
=> Loaded: undir_indices.npy
=> Loaded: undir_indeg_vec.npy
=> Graph loaded: 1.24 secs.

[18:56:44] Computing REL-KLINKER for 5 triples..
[18:56:50] time: 3.35s
1. Working on (2985653, 599, 3218267)..[18:56:55] time: 2.90s
 2. Working on (2734002, 599, 5305646)..[18:56:57] time: 2.18s
 3. Working on (5140024, 599, 4567127)..[18:57:00] time: 2.16s
 4. Working on (1522148, 599, 1357357)..[18:57:02] time: 2.15s
 5. Working on (4319468, 599, 2450828)..[18:57:03] 
[18:57:03] * Saved results: knowledgestream/output/out_relklinker_sample_2017-08-23.csv
[18:57:03] Relklinker computation complete. Time taken: 18.68 secs.
```
and a CSV file is created at the specified output directory, which contains `score` and `softmaxscore` (normalized) for each triple.




