
[![forthebadge](http://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](http://forthebadge.com)

Overview
--------

netrankr is an R package that can be used for centrality analyses of networks. Although it implements some indices, the main focus lies on an index-free assessment of centrality. Most implemented methods are, however, more general and can be used whenever partial rankings have to be analysed

Install
-------

``` r
require(devtools)
install_github("schochastics/netrankr")
```

Details
-------

Some features of the package are:

-   Working with the neighborhood inclusion preorder. This forms the bases for any centrality analysis on undirected and unweighted graphs. More details can be found in the dedicated vignette: `vignette("neighborhood_inclusion",package="netrankr")`.
-   Constructing graphs with a unique centrality ranking. This class of graphs, known as threshold graphs, can be used to benchmark centrality indices, since they only allow for one ranking of the nodes. For more details consult the vignette: `vignette("threshold_graph",package="netrankr")`.
-   Probabilistic ranking methods. The package includes several function to perform probabilistic rank analyses of nodes in a network. These include expected ranks and relative rank probabilities (how likely is it that a node is more central than another). An extensive example is given in the corresponding vignette (TODO). }

To browse all vignettes use: `browseVignettes(package = "netrankr")`

Notable functions
-----------------

-   `neighborhood_inclusion` and `positional_dominance` can be used to construct partial orders on a network. While `neighborhood_inclusion` is very specific (undirected, unweighted networks), `positional_dominance` can be used with any kind of input network. If cost variables (e.g. distances) are used, set `benefit=FALSE`. If actor identities don't matter set `map=TRUE`. Consult the respective vignettes for more detailed explanations.
-   `threshold_graphs` constructs a random uniquely ranked graph. That is, a graph where all centrality indices yield the same ranking.
-   `rank_analysis` performs a complete rank analysis of a network, including expected ranks and relative rank probabilities (how likely is it that a node is more central than another?) as well as the number of possible centrality rankings.

Caveats
-------

Finding/Enumerating all linear extension of a partial order is \#P-complete, so care has to be taken with larger networks to not run into memory problems. The package includes some approximate methods (found with `approx_`) that work even on huge networks.
