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

