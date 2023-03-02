# Reconstruct Maximum-Likelihood from an alignment

```js
iqtree -s alignment.phy
```

# Choose the substitution model

```js
iqtree -s example.phy -m MFP
```

The command above will indicate the proper model using ModelFinder *while undergoing tree reconstruction*, and will give an outcome named **example.phy.model**.
Substitution models can be checked here: http://www.iqtree.org/doc/Substitution-Models

If you want to run only the model test, you can use:

```j
iqtree -s example.phy -m MF
```

Other functions:

```js
-cmax (maximum number of categories tested)
-mset (resticts to a subset of base models)
-mtree (calls for a more robust analysis invoking a full tree search, but requiring more computational power)
```

For SNP data (DNA) that typically do not contain constant sites, you can explicitly tell the model to include ascertainment bias correction: **+ASC**

# Assessing branch-support (Ultra-fast bootstrap)

```js
iqtree -s example.phy -m TIM2+I+G -B 1000
# for version 1.x change -B to -bb
```

Outputs:

```js
example.phy.iqtree: shows a textual representation of the maximum likelihood tree with branch support values in percentage
example.phy.contree: the consensus tree with assigned branch supports where branch lengths are optimized on the original alignment.
example.phy.splits.nex: support values in percentage for all splits (bipartitions), computed as the occurence frequencies in the bootstrap trees. This file can be viewed with the program SplitsTree to explore the conflicting signals in the data. So it is more informative than consensus tree, e.g. you can see how highly supported the second best conflicting split is, which had no chance to enter the consensus tree.
example.phy.splits (if using -wsplits option): This file contains the same information as example.phy.splits.nex but in star-dot format.
```


