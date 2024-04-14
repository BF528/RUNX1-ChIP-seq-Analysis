#ChIPseq
##Methods:
ChIP-seq data from two paired experiments was downloaded. Initial quality control was performed using FASTQC v0.12.1-0 [ref]. Adapter trimming was conducting using Trimmomatic v0.39 [ref] with parameters: ILLUMINACLIP:{adapters}:2:30:10 LEADING:3 TRAILING:3 SLIDINGWINDOW:4:15. Bowtie2 [2] v2.5.3 was used to generate a genome index for the mouse primary assembly genome (GRCm39, release m34). Reads were aligned to GRCm39, release m34 using bowtie2 with default parameters. Alignments were sorted and indexed with SAMtools v1.19.2 [ref] using default parameters. QC was performed on sorted alignments using SAMtools and MultiQC v1.20 [ref] with default parameters. Peak calling was performed on each replicate with HOMER v4.11 [ref] findPeaks using the -style parameter. Reproducible peaks were generated with bedTools v2.31.1 [ref] using peaks with at least 50% overlap. Peaks in genomic blacksite regions of the hg39 build of the genome were filtered out using bedTools subtract with default parameters. Peak annotation was performed with HOMER annotatePeaks.pl using the version M34 primary assembly annotation gtf. Motif finding was performed with HOMER findMotifsGenome.pl and the GRCm39 primary assembly genome.

##Questions to Address:
1.	Briefly remark on the quality of the sequencing reads and the alignment statistics, make sure to specifically mention the following:
	Are there any concerning aspects of the quality control of your sequencing reads?
	Are there any concerning aspects of the quality control related to alignment?
	Based on all of your quality control, will you exclude any samples from further analysis?
2.	After QC, please generate a “fingerprint” plot (see deeptools utility) and a heatmap plot of correlation values between samples (see project 2)
	Briefly remark on the plots and what tjey indicates to you in terms of the experiment
3.	After performing peak calling analysis, generating a set of reproducible peaks and filtering peaks from blacklisted regions, please answer the following:
	How many peaks are present in each of the replicates?
	How many peaks are present in your set of reproducible peaks? What strategy did you use to determine “reproducible” peaks?
	How many peaks remain after filtering out peaks overlapping blacklisted regions?
4.	After performing motif analysis and gene enrichment on the peak annotations, please answer the following:
	Briefly discuss the main results of both of these analyses and what they might imply about the function of the factor we are interested in.

##Deliverables
1.	Produce a heatmap of correlation values between samples (see project 2)
2.	Generate a “fingerprint” plot using the deeptools plotFingerprint utility
3.	Create a figure / table containing the number of peaks called in each replicate, and the number of reproducible peaks
4.	A single BED file containing the reproducible peaks you determined from the experiment.
5.	Perform motif finding on your reproducible peaks
	Create a single table / figure with the most interesting results
6.	Perform a gene enrichment analysis on the annotated peaks using a well-validated gene enrichment tool
	Create a single table / figure with the most interesting results
7.	Produce a figure that displays the proportions of where the factor of interest is binding (Promoter, Intergenic, Intron, Exon, TTS, etc.)


