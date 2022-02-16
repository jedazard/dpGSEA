# dpGSEA
Drug Perturbation GSEA


==================
### Website

This is a mirror of [Mike Fang's GitHub repository](https://github.com/sxf296/drug_targeting). 
Please contact Mike Fang at sxf296@case.edu or Mark Cameron at mjc230@case.edu for any questions.


==================
### Requirements - Dependencies

   + Python2 or Python3 (version >= 0.9.3) 
   + Modules `numpy` and `pandas`


==================
### Description

A drug-gene target enrichment technique utilizing a modified GSEA approach, and uses prior drug-defined 
gene sets in the form of proto-matrix (pm) files: these are derived from either CMAP or L1000 database 
labeled as L1K or CM respectively. The designation PXX following the label gives the size of the signatures 
defined within.

==================
### How to use

python dpGSEA.py -h for help

The following flags are listed below:

* -tt TOPTABLE, --toptable TOPTABLE (This refers to the TopTable limma output, but one could use any ranked table as long as there are columns "logFC" and "t")
* -dr DRUGREF, --drugref DRUGREF (This refers to the proto-matrix: PM_L1000_FC20.csv, PM_L1000_FC50.csv, etc.)
* -ma, --match (indicating whether to search for matching profiles)
* -i ITERATIONS (we recommend, at least 1000 iterations for generating significance, default is at 1000)
* -sd SETSEED, --setseed SETSEED
* -o OUT, --out OUT (output file names, results will be tab delimited)

Toy example: 

python dpGSEA.py -tt CD71.csv -dr pms/L1K_P10.csv -i 1000 -o results.tsv



==================
### Output file

* drug - specific drug
* ES - enrichment score
* NES - normalized enrichment score
* ES_p - enrichment score p value
* TCS - target compatibility score
* NTCS - normalized target compatibility score
* TCS_p - target compatibility score p value
* genes - leading edge genes
* NTCS_num - FDR cutoff for NTCS, denoted with 1 if drug reaches sig. threshold at default 0.90 and 0.95 confidence levels.
* NES_num - FDR cutoff for NES

Please note, to add different FDR cutoffs, please ctrl+F "quantiles = [90, 95]" within the script and add confidence levels as needed.


==================
### Results

* Enrichment score (ES) - this score is interpreted the same way the standard GSEA enrichment score. It reflects the degree to which a complementary or matching drug gene profile is overrepresented at the top of a ranked list.

* Enrichment score p-value (ES_pvalue) - the statistical significance of the enrichment score for a single drug gene set.

* Target compatibility p-value (TC_pvalue) - a p-value reflecting the quantity and magnitude of statistical significance of differentially expressed genes that match or antagonize a drug profile. This statistical test compares the modulation of the leading edge genes against random modulation.

* Driver Genes aka leading edge genes (driver_genes) - this lists genes that appear in the ranked list at or before the point at which the running sum reaches its maximum deviation from zero. These genes are often interpreted as the genes driving an enrichment or modulation of drug-gene and differential expression analysis.


===================
### Acknowledgments

Authors: 
   + Mike Fang, Ph.D. <sxf296@case.edu>
   + Brian Richardson, Ph.D. <bxr183@case.edu>
   + Cheryl Cameron, Ph.D. <cxc724@case.edu>
   + Jean-Eudes Dazard, Ph.D. <jean-eudes.dazard@case.edu>
   + Mark Cameron, Ph.D. <mark.cameron@case.edu>

Author’s Contributions: 
   + MF: method design, computational analysis and testing, and manuscript writing. 
   + BR: bioinformatic analysis and validation. 
   + CMC: design, biological validation, and manuscript writing. 
   + JED: methods development and manuscript writing. 
   + MJC: principal investigator, direction and funding of project, manuscript writing.Maintainers: 
   + Mike Fang, Ph.D. <sxf296@case.edu>

Funding/Provision/Help:   
   + This work made use of the High Performance Computing Resource in the Core Facility for Advanced Research Computing at Case Western Reserve University. 
   + This research was partially supported by NHLBI/NIH under award number T32HL007567, and the content is the responsibility of the authors and does not necessarily 
     represent the official views of the NIH. We also gratefully acknowledge the support of the Case/UHC Center for AIDS research (P30AI036219 for MJC), 
     and the Psoriasis Center of Research Translation (P50AR070590 for authors MJC and MF).


==================
### References

   + Fang M., Richardson B., Cameron C.M., Dazard J-E., and Cameron M.J.  
      *Drug perturbation gene set enrichment analysis (dpGSEA): a new transcriptomic drug screening approach*.
      BMC Bionformatics (2021), 22(1):1-14.
