# _ggtree_ a package for plotting phylogenetic trees

1. Questions:
- How do I render and annotate a tree from an existing tree file?
2. Objectives:
- Understanding the basics of _ggtree_
- Annotating Nodes
- Grouping Clades
3. Keypoints:
- ggtree is a relative of ggplot for trees
- ggtree contains many geoms for annotating trees

## `ggtree` - a Bioconductor package for displaying phylogenetic trees

Bioconductor is a (very) large set of libraries for operating on biological data types [https://www.bioconductor.org/](https://www.bioconductor.org/) . `ggtree` is a library inspired by `ggplot` for drawing trees.  Much of what we've already seen in `ggplot` is transferrable to `ggtree` so the syntax should be familiar.

> ## Installing `ggtree`
> Installing bioconductor takes a long time and isn't done in the same way as with other R packages. To install first  run this special script in the R console (making sure you have an internet connection) :
> `source("https://bioconductor.org/biocLite.R")` in the R console (making sure you have an internet connection). 
> Bioconductor libraries can then be installed with the `biocLite()` function 
> `biocLite("ggtree")

`ggtree` takes a range of common tree formats as input. We'll use a sample file in `newick` format. This creates a special sort object called a 'phylo' object that knows all sorts of information about the tree.


```r
library(ggtree)
```

```
## ggtree v1.14.6  For help: https://guangchuangyu.github.io/software/ggtree
## 
## If you use ggtree in published research, please cite the most appropriate paper(s):
## 
## - Guangchuang Yu, David Smith, Huachen Zhu, Yi Guan, Tommy Tsan-Yuk Lam. ggtree: an R package for visualization and annotation of phylogenetic trees with their covariates and other associated data. Methods in Ecology and Evolution 2017, 8(1):28-36, doi:10.1111/2041-210X.12628
## 
## - Guangchuang Yu, Tommy Tsan-Yuk Lam, Huachen Zhu, Yi Guan. Two methods for mapping and visualizing associated data on phylogeny using ggtree. Molecular Biology and Evolution 2018, accepted. doi: 10.1093/molbev/msy194
```

```r
tree <- read.tree("data/mammals.nwk")
str(tree)
```

```
## List of 4
##  $ edge       : int [1:13, 1:2] 9 10 10 9 11 12 12 11 13 14 ...
##  $ edge.length: num [1:13] 0.846 19.2 6.8 3.874 7.53 ...
##  $ Nnode      : int 6
##  $ tip.label  : chr [1:8] "raccoon" "bear" "sea_lion" "seal" ...
##  - attr(*, "class")= chr "phylo"
##  - attr(*, "order")= chr "cladewise"
```
The tree can be drawn using the `geom_tree()` function.


```r
ggplot(tree) + geom_tree()
```

<img src="09-phylogenetic_trees_files/figure-html/unnamed-chunk-2-1.png" width="672" />

There is a special theme that sorts out the background for trees:


```r
ggplot(tree) + geom_tree() + theme_tree()
```

<img src="09-phylogenetic_trees_files/figure-html/unnamed-chunk-3-1.png" width="672" />
And because you nearly always want these three `ggtree` provides a utility function to do all of that - `ggtree()`

```r
ggtree(tree)
```

<img src="09-phylogenetic_trees_files/figure-html/unnamed-chunk-4-1.png" width="672" />

With this function we can add layout options

```r
ggtree(tree, layout = "circular")
```

<img src="09-phylogenetic_trees_files/figure-html/unnamed-chunk-5-1.png" width="672" />

### Labels
Adding labels to treetips is done with the `geom_tiplab()` geom.

```r
ggtree(tree) + geom_tiplab(size=3, color="purple")
```

<img src="09-phylogenetic_trees_files/figure-html/unnamed-chunk-6-1.png" width="672" />

Adding the nodes is done with special options to the `geom_point()` geom. The shape and colour aesthetics are set to the variable `isTip` which is an internal variable in the tree object.


```r
p <-  ggtree(tree) + geom_tiplab(size=3, color="purple")
p + geom_point(aes(shape=isTip, color=isTip), size=3)
```

<img src="09-phylogenetic_trees_files/figure-html/unnamed-chunk-7-1.png" width="672" />

### Annotating and colouring clades
More useful is the ability to colour particular bits of the tree. First let's add a highlight bar to the side of the tree highlighting the sea mammal family. To do this we need to find the first node in the tree common to the clade we want to highlight. For this it's node number 12 and we use the `geom_cladelabel()` geom to add. We can use multiple `geom_cladelabel()` layers for more labels.


```r
p + geom_cladelabel(node=12, label="Sea Mammals")
```

<img src="09-phylogenetic_trees_files/figure-html/unnamed-chunk-8-1.png" width="672" />
You can also use blocks of colour for this:

```r
p + geom_hilight(node=12, fill="steelblue", alpha=.6)
```

<img src="09-phylogenetic_trees_files/figure-html/unnamed-chunk-9-1.png" width="672" />

To actually find the node number we need we can use the `MRCA()` function and pass it a list of labels we want the most recent common ancestor for

```r
MRCA(tree, tip=c('seal','sea_lion'))
```

```
## [1] 12
```


You can use this information to colour different parts of the tree, too. First you need to mark the tree objects as having a new `group` factor with the `groupClade()`, function and then dynamically colour by the new group factor






