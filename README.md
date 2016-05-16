# PhyloD
##### Machine learning tools for modeling viral adaptation to host immune responses

HIV, like most retroviruses, is characterized by a tremendous rate of mutation, which leads to a high level of genetic diversity within and among patients. This genetic variation is the substrate for rapid within-host evolution. As our immune system learns to target the virus, the virus adapts, leading to an endless game of cat-and-mouse. From a scientific perspective, this provides a useful opportunity: if HIV is contantly adapting to our individual immune responses, then studying HIV adaptation will provide insights into both virus function and basic immunology. Over the years, we have developed models of viral adaptation that have allowed us to do just that. This repo includes a subset of those tools.

__Our most popular tools are exposed as a web app at http://phylod.research.microsoft.com__

__Use the [Release tab](https://github.com/Microsoft/PhyloD/releases) to download precompiled (for windows) binaries.__


### Publications

These tools have been used in many publications. Within each release is a set of batch scripts for running examples. Each batch script contains the primary publication that should be cited. Please follow those guidelines. 

A partial list of publications that use these tools is available [here](http://research.microsoft.com/en-us/um/people/carlson/publications.html).

### Partial list of tools included in this release
These tools (and many others) are included in this release. The ones below have example batch files included in the precompiled binaries. Adaptation and transmission index are included on the web app.

* __Find HLA-mediated escape associations.__ The original PhyloD tool, for finding "escape associations" while correcting for phylogenetic relatedness. This code was initially implemented in our _Phylogenetics Dependency Networks_ paper  ([primary citationin PLoS Comp Biol](http://dx.doi.org/10.1371/journal.pcbi.1000225)), then was modified to use phylogenetically corrected logistic regression as the primary probability distribution in [this paper](http://jvi.asm.org/content/86/9/5230.full). The code included in this repo will identify associations on a local machine. This works ok if you're not worried about covariation. Covariation requires big compute, which we'll be releasing at a later date. Use this tool to identify escape associations.
* __Compute HLA adaptation.__ This tool builds on the associations by estimating the conditional probability `Pr(sequence | HLA)` for any HIV sequence given any HLA (in your training set). This tool was published in our _Impact of pre-adaptated HIV-1 transmission_ Nature Medicine paper ([primary citation and more details](http://research.microsoft.com/~carlson/papers/adaptation15.html)). These "adaptation scores" provide a useful summary statistic for how adapted any sequence is to any individual or HLA allele. This summary statistic correlates with viral load and CD4 counts, both when looking at autologous virus, and when looking at founder virus. It also predicts vaccine response magnitudes (vaccine inserts that carry lots of escapes for an individual will not elicity as many responses in that individual). We also include the closely related __HLA similarity__ tool, which estimates how similar two HLA alleles (or two individuals) are based on the correlation of their adaptation scores over a reference panel of viruses.
* __Transmission Index.__ This tool is a partial code release from our _Selection bias at the heterosexual HIV-1 transmission bottleneck_ Science paper ([primary citation and more details](http://research.microsoft.com/en-us/um/people/carlson/papers/selectionBias14.html)). The full source code for that paper was a mix of C#, R and Matlab. Here we include the C#, which allows computation of the transmission index on a given set of sequences. For this, we use the model weights transcribed from  Table 2 of that paper. In that paper, we showed that viruses with higher predicted fitness are more likely to be transmitted. Theoretically, this selection increases when you're at reduced risk of infection, and we showed that empirically when comparing men vs women and men with or without genetical inflammation. The transmission index simply averages the model weights over all sites in a sequence, yielding a single score for each protein. We showed this was weakly linked with odds of transmission. More recently, Todd Allen's group showed that (as predicted), the transmission index is higher among the founder viruses of heterosexual men compared to men who have sex with men (MSM). This tool is best used for similar studies, in which the hypothesis is that the founder virus of a group with lower risk of infection has higher transmission index compared to another group.

### Compiling the code

_We aim to get the source code up in the coming weeks._

### Contact

Please send all questions and comments to phylod@microsoft.com
