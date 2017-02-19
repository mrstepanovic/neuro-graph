# About
Graph theory provides a useful way to measure and describe functional network structure in the brain ([Gits, 2016][1]). Unfortunately, a high barrier to entry has hindered its utilization in cognitive neuroscience. Neuro Graph offers a streamlined process for analyzing functional networks with graph theory, and in future versions aims to improve upon existing visualization methods for functional networks.

Bespoke for the [Frontotemporal Disorders Unit](http://www.nmr.mgh.harvard.edu/~bradd/) at Massachusetts General Hospital/Harvard Medical School, Boston, MA.

[1]: http://bit.ly/2jC0AFq 

# Background
## Graph Theory and Social Network Analysis
Almost any system can be represented in terms of entities and the relationships between them. Therefore, it is no surprise that contemporary network analysis is the culmination of several fields of academic research. One important tip when analyzing networks is being very clear about the terminology being used. For instance, while __graph theory__ is a branch of mathematics that represents entities and relationships as "vertices" and "edges" ([Dickson, 2006][2]), the sociological field of __social network analysis__ refers to these as "nodes" and "ties", or sometimes "actors" and "links" ([Butts, 2008][3]). Collectively, vertices and edges are referred to as "graphs" or "networks". In the context of analyzing large-scale, functionally connected networks in the brain, we will refer to brain regions as "nodes", relationships between nodes as "connections" and the overall system as a "network". 

## How neuro-graph works in the lab's fcMRI analysis ecosystem
Neuro-graph will use output from the NRG fc-analysis script: the adjacency matrix of Pearson's r values between ROIs. This adjacency matrix represents the strength of connections between all nodes in the network. These values can then be limited by an alpha threshold and used in a neuro-graph analysis. Neuro-graph is built upon R's open source ([statnet][4]) library.

### Analysis routine summarized in [Fellini et al. (2014)][5]
![Fellini analysis routine](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4150298/bin/rstb20130521-g1.jpg)

### Simplified neuro-graph analysis routine
![neuro-graph analysis routine](http://i.imgur.com/CGNGesS.png)



[2]: https://www.math.utah.edu/mathcircle/notes/MC_Graph_Theory.pdf
[3]: http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.455.1587&rep=rep1&type=pdf
[4]: http://statnet.org/
[5]: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4150298/

## Different Levels of Variables and Analysis

Just as there are multiple levels of analysis in human subjects research, there are multiple levels of analysis in network analysis. A property which describes an individual node is called a node level index (NLI), while a property that describes the entire graph is called a graph level index (GLI). NLIs tend to describe how important, or "central" a node is based on how many connections it has, how many connections its connections have, the average number of steps it must take to reach all other nodes, and the extent to which it maintains the integrity of the macro-level graph structure ([Freeman, 1979][4]). Similarly, GLIs can describe the density of a network's connections, the extent to which a network structure is hierarchical, and the average number of connections all nodes have in the network ([Anderson et al., 1999][5]). There are dozens of NLIs and GLIs, only a fraction of which might be relevant in the context of functional brain connectivity. In most analysis, GLIs will be of far greater interest than NLIs.

[4]: http://leonidzhukov.net/hse/2014/socialnetworks/papers/freeman79-centrality.pdf
[5]: www.cs.cmu.edu/~brigham/papers/social1999.pdf

## NLIs Used in fcMRI Research

## GLIs Used in fcMRI Research


# TODO
- ~~Create Dropbox link for reference literature~~
- Review literature
-- Determine node and graph level indices (NLIs; GLIs) of topical interest
-- Identify knowledge gaps in the field
-- Centralize prereqs for learning these techniques
- List all assumptions of input data when using this software
- Decide on input and output filetypes
- Plan a data flow chart

# Feature wish list (keep these cited, if possible)
- Output NLIs, GLIs
- Contextual links to more information about each measure
- Save output as file
- Automatic atlas-based ROI generation
-- Freesurfer atlases
-- AAL
-- Harvard/Oxford
- Dynamic network measures?
-- Maybe just cross-sectional tests for modulation
- visualization (the big one)
-- nodes AND edges
-- enable colorized factors (network subcomponents?)
-- 3D rotation would be nice
