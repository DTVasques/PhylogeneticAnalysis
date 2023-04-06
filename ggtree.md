# Install packages

```js
install.packages('ggimage')
install.packages("rlang")

library(BiocManager)
BiocManager::install("ggtree")


devtools::install_github("YuLab-SMU/ggtree")
```

# Documentation

```js
browseVignettes("ggtree")

library("ggimage")
library("ggtree")
library("treeio")
library("ape")
```
#  Read tree file

```js
tree <- read.tree("test.nwk")
```

# Plot the tree
```js
ggplot(tree, aes(x, y)) + geom_tree() + theme_tree()
```

# Change the color, size and type
```js
ggtree(tree, color="firebrick", size=2, linetype="dotted")
```

# Remove branch length
```js
ggtree(tree, branch.length="none")
```

# layouts
```js
ggtree(tree)
ggtree(tree, layout="roundrect")
ggtree(tree, layout="slanted")
ggtree(tree, layout="ellipse")
ggtree(tree, layout="circular")
ggtree(tree, layout="fan", open.angle=120)
ggtree(tree, layout="equal_angle")
ggtree(tree, layout="daylight")
ggtree(tree, branch.length='none')
ggtree(tree, layout="ellipse", branch.length="none")
ggtree(tree, branch.length='none', layout='circular')
ggtree(tree, layout="daylight", branch.length = 'none')
```

# Modify scale/ coordinates
```js
ggtree(tree) + scale_x_reverse()
ggtree(tree) + coord_flip()
ggtree(tree) + layout_dendrogram()
ggplotify::as.ggplot(ggtree(tree), angle=-30, scale=.9)
ggtree(tree, layout='slanted') + coord_flip()
ggtree(tree, layout='slanted', branch.length='none') + layout_dendrogram()
ggtree(tree, layout='circular') + xlim(-10, NA)
ggtree(tree) + layout_inward_circular()
ggtree(tree) + layout_inward_circular(xlim=15)
```

## Displaying tree components
# Tree scale
```js
ggtree(tree) + geom_treescale()
```

# Treescale components include:
```js
#x and y for treescale position
#width for the length of the treescale
#fontsize for the size of the text
#linesize for the size of the line
#offset for relative position of the line and the text
#color for color of the treescale
```

```js
ggtree(tree) + geom_treescale(x=0, y=45, width=1, color='red')
ggtree(tree) + geom_treescale(fontsize=6, linesize=2, offset=1)
```

# Displaying nodes/ tips

```js
ggtree(tree) + 
  geom_point(aes(shape=isTip, color=isTip), size=3)

p <- ggtree(tree) + 
  geom_nodepoint(color="#b5e521", alpha=1/4, size=10) 
p + geom_tippoint(color="#FDAC4F", shape=8, size=3)
```

# Display labels

```js
p + geom_tiplab(size=3, color="purple")

ggtree(tree, layout="circular") + geom_tiplab(aes(angle=angle), color='blue')
```

## with root-edge = 1
```js
tree1 <- read.tree(text='((A:1,B:2):3,C:2):1;')
ggtree(tree1) + geom_tiplab() + geom_rootedge()
```

## without root-edge
```js
tree2 <- read.tree(text='((A:1,B:2):3,C:2);')
ggtree(tree2) + geom_tiplab() + geom_rootedge()
```

## setting root-edge
```js
tree2$root.edge <- 2
ggtree(tree2) + geom_tiplab() + geom_rootedge()
```

## specify the length of root edge for just plotting
## this will ignore tree$root.edge
```js
ggtree(tree2) + geom_tiplab() + geom_rootedge(rootedge = 3)
```

# Theme the tree
```js
ggtree(tree, color="orange", size=1) + theme_tree('grey30')
ggtree(tree, color="#0808E5", size=1) + theme_tree("#FEE4E9")
```
