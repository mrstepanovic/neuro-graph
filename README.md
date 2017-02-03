# About
Graph theory provides a useful way to measure and describe functional network structure in the brain ([Gits, 2016][1]).
Unfortunately, a high barrier to entry has hindered its utilization in cognitive neuroscience. Neuro Graph offers 
a streamlined process for analyzing functional networks with graph theory, and in future versions aims to improve
upon existing visualization methods for functional networks.

Bespoke for the [Frontotemporal Disorders Unit](http://www.nmr.mgh.harvard.edu/~bradd/) at Massachusetts General Hospital/Harvard Medical School, Boston, MA.

[1]: http://bit.ly/2jC0AFq 

# Background
## Graph Theory and Social Network Analysis
Almost any system can be represented in terms of entities and the relationships between them. Therefore, it is no surprise that
contemporary network analysis is the culmination of several fields of academic research. One important tip when analyzing networks
is being very clear about the terminology being used. For instance, while __graph theory__ is a branch of mathematics that represents 
entities and relationships as "vertices" and "edges" ([Dickson, 2006][2]), the sociological field of __social network analysis__ refers to these as "nodes" and "ties", or sometimes "actors" and "links" ([Butts, 2008][3]). Collectively, vertices and edges are referred to as "graphs" or "networks". In the context of analyzing large-scale, functionally connected networks in the brain, we will refer to brain regions as "nodes", relationships between nodes as "connections" and the overall system as a "network". 

[[insert picture of neuro graph here]]

[2]: https://www.math.utah.edu/mathcircle/notes/MC_Graph_Theory.pdf
[3]: http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.455.1587&rep=rep1&type=pdf

## Different Levels of Analysis


# To Do
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
