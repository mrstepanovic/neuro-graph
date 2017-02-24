# About
Graph theory provides a useful way to measure and describe functional network structure in the brain ([Gits, 2016][1]). Unfortunately, a high barrier to entry has hindered its utilization in cognitive neuroscience. Neuro Graph offers a streamlined process for analyzing functional networks with graph theory, and in future versions aims to improve upon existing visualization methods for functional networks.

Bespoke for the [Frontotemporal Disorders Unit](http://www.nmr.mgh.harvard.edu/~bradd/) at Massachusetts General Hospital/Harvard Medical School, Boston, MA.

[1]:http://bit.ly/2jC0AFq 

# Background
## Graph Theory and Social Network Analysis
Almost any system can be represented in terms of entities and the relationships between them. Therefore, it is no surprise that contemporary network analysis is the culmination of several fields of academic research. One important tip when analyzing networks is being very clear about the terminology being used. For instance, while __graph theory__ is a branch of mathematics that represents entities and relationships as "vertices" and "edges" ([Dickson, 2006][2]), the sociological field of __social network analysis__ refers to these as "nodes" and "ties", or sometimes "actors" and "links" ([Butts, 2008][3]). Collectively, vertices and edges are referred to as "graphs" or "networks". In the context of analyzing large-scale, functionally connected networks in the brain, we will refer to brain regions as "nodes", relationships between nodes as "connections" and the overall system as a "network". A review by [Fellini et al. (2014)][5] summarizes the traditional analysis procedure for network data in neuroscience:

![Fellini analysis routine](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4150298/bin/rstb20130521-g1.jpg)

## How neuro-graph works in the lab's fcMRI analysis ecosystem
Neuro-graph will simplify or even automate this process using existing infrastructure in the Dickerson Neuroimaging Lab and MGH Memory Disorders Unit. For resting-state functional network analysis, it uses output from the NRG fc-analysis script: the adjacency matrix of Pearson's r values between ROIs. This adjacency matrix represents the strength of connections between all nodes in the network. These values will be binarized by an a-priori threshold (a) and used to represent the underlying functional network (b). Neuro-graph will accomplish this with the open source ([statnet][4]) library for R.

![Matrix to graph](http://i.imgur.com/CcuR1Ec.jpg)

The overall processing routine would be as follows:

![neuro-graph analysis routine](http://i.imgur.com/KtlvQT1.jpg)

[2]:https://www.math.utah.edu/mathcircle/notes/MC_Graph_Theory.pdf
[3]:http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.455.1587&rep=rep1&type=pdf
[4]:http://statnet.org/
[5]:https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4150298/

## Different Levels of Variables and Analysis

Just as there are multiple levels of analysis in human subjects research, there are multiple levels of analysis in network analysis. A property which describes an individual node is called a node level index (NLI), while a property that describes the entire graph is called a graph level index (GLI). NLIs tend to describe how important, or "central" a node is based on how many connections it has, how many connections its connections have, the average number of steps it must take to reach all other nodes, and the extent to which it maintains the integrity of the macro-level graph structure ([Freeman, 1979][4]). Similarly, GLIs can describe the density of a network's connections, the extent to which a network structure is hierarchical, and the average number of connections all nodes have in the network ([Anderson et al., 1999][5]). There are dozens of NLIs and GLIs, only a fraction of which might be relevant in the context of functional brain connectivity. In most analyses, GLIs, or "global network measures", will be of far greater interest. A selection of these indicators are described in the next section.

[6]:http://leonidzhukov.net/hse/2014/socialnetworks/papers/freeman79-centrality.pdf
[7]:www.cs.cmu.edu/~brigham/papers/social1999.pdf

## Common Network Measures Used in Neuroscience Research ([Rubinov and Sporns, 2010][12])

We will use the hypothetical network representation above to describe each indicator below.

[12]: http://www.sciencedirect.com/science/article/pii/S105381190901074X

### Measures of Integration

* Characteristic path length ([Watts and Strogatz, 1998][8])
The average distance between any two pairs of nodes, computed for all node pairs in the network.
![Characterisitc Path Length](http://i.imgur.com/mIk8Aif.jpg)

* Global efficiency ([Latora and Marchiori, 2001][9])
A measure of how efficiently a network can exchange information. Comparable to (1/average path length). In our case, imagine an action potential being generated at random for any node. All nodes have an equal probability of generating the AP. How long would it take the AP to diffuse through the entire network? From node E, probably quite quickly. From node G, a bit longer.

[8]:http://www.nature.com/nature/journal/v393/n6684/full/393440a0.html
[9]:https://www.w3.org/People/Massimo/papers/2001/efficiency_prl_01.pdf

### Measures of Segregation

* Clustering coefficient ([Watts and Strogatz, 1998][8])
The degree to which nodes tend to cluster together. Essentially calculated as the number of total 2-paths (incompleted triangles) in a graph divided by the number of closed 2-paths (completed triangles). Note: permutations of triangle vertices are calculated as different triangles: A-B-C, B-A-C, and C-A-B count as 3 closed 2-paths.
![Clustering Coefficient](http://i.imgur.com/dgAFDtX.jpg)

* Transitivity ([Newman, 2003][10])
The degree to which two-paths tend to be closed (form a triangle). Differs from clustering coefficient only in the way graph nodes are sampled during calculation. Clustering coefficient is a more common metric in contemporary network science. [http://pages.stat.wisc.edu/~karlrohe/netsci/MeasuringTrianglesInGraphs.pdf][(more info)]

* Local efficiency ([Latora and Marchiori, 2001][9])


* Modularity ([Newman, 2006][11])
Modularity is a quality function whose optimization represents partitioned communities, or clusters, or points. Newman's method computes eigenvectors over an adjacency matrix, resulting in a "modularity matrix" for spectral analysis. Analogous to k-means and k-nearest neighbors clustering. 
![Modularity with 3 Modules](http://i.imgur.com/EdBxY7g.jpg)

[10]:http://math.uchicago.edu/~shmuel/Network-course-readings/Newman,%20SIAM.pdf
[11]:http://www.pnas.org/content/103/23/8577.full

### Measures of Centrality
* Closeness centrality ([Freeman, 1978][6])
* Betweenness centrality ([Freeman, 1978][6])
* Within-module degree z-score ([Guimera and Amaral, 2005][13])
* Participation coefficient ([Guimera and Amaral, 2005][13])

[13]:https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2151742/

## Measures of Resilience
* Degree distribution ([Barabasi and Albert, 1999][14])
* Average neighbor degree ([Pastor-Satorras et al., 2001][15])
* Assortativity coefficient ([Newman, 2002][16])
* Measure of network "small-worldness" ([Humphries and Gurney, 2008][17])

[14]:http://barabasi.com/f/67.pdf
[15]:http://journals.aps.org/prl/abstract/10.1103/PhysRevLett.86.3200
[16]:https://arxiv.org/abs/cond-mat/0205405
[17]:http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0002051

# TODO
- ~~Create Dropbox link for reference literature~~
- ~~Review literature~~
- ~~Determine node and graph level indices (NLIs; GLIs) of topical interest~~
- Identify knowledge gaps in the field
- Centralize prereqs for learning these techniques
- List all assumptions of input data when using this software
- Decide on input and output filetypes
- ~~Plan a data flow chart~~

# Feature wish list (keep these cited, if possible)
- Output NLIs, GLIs
- Contextual links to more information about each measure
- Save output as file
- Automatic atlas-based ROI generation
- Freesurfer atlases
- AAL
- Harvard/Oxford
- Dynamic network measures?
- Maybe just cross-sectional tests for modulation
- visualization (the big one)
- nodes AND edges
- enable colorized factors (network subcomponents?)
- 3D rotation would be nice
- [Brain Net Viewer on NITRC][18]
- [Graph Analysis Toolbox Software (for Matlab) on NITRC][19]

[18]:https://www.nitrc.org/projects/bnv
[19]:https://www.nitrc.org/projects/gat/
