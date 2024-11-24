# Tips for research project
The research project is open-ended, and you are encouraged to be creative and follow your own interests. However, many students end up wanting to use common types of data and resources, so I have gathered frequently used advice and links here. They are organized according to the data type. This list is far from exhaustive; it is merely scratching the surface of what is available online.
  
## Data sources

### Raw shotgun data for assembly

* Individual bacterial (or other) genome shotgun data
  * You can search the NCBI Sequence Read Archive (SRA) database for a particular organism: https://www.ncbi.nlm.nih.gov/sra. For example, if you search "Salmonella", you will find thousands of shotgun sequencing data sets. You can filter by technology, e.g. Illumina for short-read data. To download the raw sequencing data, click on the data set link, then click the link under "Run" at the bottom of the page, then click "FASTA/FASTQ download" at the top, then select "Filtered", then "FASTA. This will download the raw sequencing file. Note: When the data set is paired-end, even though you get one FASTA file, the forward and reverse reads are interleaved. You could treat them as single-end reads, but assembly will work better if you treat them as paired-end (because the assembler knows the two ends belonged to the same molecule). SPADES automatically can input interleaved DNA with the "--12" flag; see here: https://ablab.github.io/spades/running.html#input-data
  * Toy data for assembly practice: Simulated data from the COVID-19 Spike protein are available in the course _Files_ folder. These are much smaller and simpler, in case you are implementing your own assembly algorithm.
* Metagenomes (mixtures of genomes) shotgun data
  * Deep shotgun metagenomics data from ~15 wild and ~15 captive Primates is available on MSI here: `/home/knightsd/public/pmp/shotgun`. The associated metadata, such as the primate species and the wild vs. captive status are in the `map.txt` file.
  * Ultra-ultra deep human metagenomics data (~2.5b paired-end reads, about 1.5TB per sample for 2 samples) are available on my CS network storage (note to self: /project/flatiron/data/uds). By request, I can move these over to the temporary "scratch" storage on MSI.
  * Raw data can be found for most published metagenomic data sets on SRA or EBI MGnify. The best way is probably to start with a publication in which you are interested, and find out where the data are deposited, usually in a section near the end called "Data Availability". Or you can go straight to the databases and search for projects. On SRA you can search for a "BioProject" with metagenomic samples, for example with [this query](https://www.ncbi.nlm.nih.gov/bioproject/?term=(%22human%20gut%20metagenome%22)%20AND%20bioproject_sra[filter]). On EBI MGnify, you can start at the [home page](https://www.ebi.ac.uk/metagenomics), click _Browse data_ > _Studies_, then enter "metagenomics" or "metagenome" in the _Filter_ field. In some cases you may not be able to find the necessary metadata (experimental variables) associated with the samples, in which case you will need to find the publication and search for a metadata table either in the supplementary materials or as a link in the Data Availability section. Be prepared for this to require non-trivial effort; acquiring and formatting published data is often one of the hardest parts. Tip: if you are having trouble finding good data sets on a particular topic (e.g. colorectal cancer), try to find a well-cited meta-analysis or review paper, and follow their citations.

### Labeled gene sequences
* Search by NCBI gene ID or gene family name: https://www.ncbi.nlm.nih.gov/gene. This is for downloading individual gene sequences, one at a time.
  * To get ideas for names of genes, you can find lists of antibiotic resistance genes and virulence genes [here](https://www.ncbi.nlm.nih.gov/pathogens/refgene/), and names of metabolic genes [here](http://www.cazy.org) (Click on an enzyme class, then a family, then click the "Characterized" tab, and use either the GenBank or UniProt links to open individual genes and download a FASTA.
* For 16s rRNA genes with taxonomic labels, you can find a dataset [here](https://ftp.microbio.me/greengenes_release/2024.09/). Specifically the taxonomy file (`...taxonomy.asv.tsv.gz`) has ASV sequences (of varying lengths) and the predicted taxonomic label. There are 23 million sequences.

### Labeled genome sequences
* Search by species name or assembly ID: https://www.ncbi.nlm.nih.gov/datasets/genome/. This will get you individual genomes, one at a time.
* Refseq has an [FTP site](https://ftp.ncbi.nlm.nih.gov/genomes/refseq/) with 100s of thousands of bacterial genomes, with useful annotations. Do not click "bacteria", because it will take forever to load. Instead, you can right-click or command-click [here](https://ftp.ncbi.nlm.nih.gov/genomes/refseq/bacteria/assembly_summary.txt) to download a table containing the species names and FTP links for all bacterial genomes in RefSeq. Once you visit an FTP link (for example, [this one](https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/003/465/715/GCF_003465715.1_ASM346571v1/)), here are some of the useful files you will see:
  * `..._feature_table.txt.gz`: table with the name, location (contig, start/end position), and NCBI ID of each predicted gene.
  * `..._cds_from_genomic.fna.gz`: the DNA sequences of the predicted genes.
  * `..._translated_cds.faa.gz`: translated amino acid sequences of the predicted genes 
  * `..._rna_from_genomic.fna.gz`: predicted non-coding RNA genes
  * `..._genomic.fna.gz`: the assembled genomic data (might be in multiple contigs)
* Use [The Genome Taxnomy Database](https://gtdb.ecogenomic.org/) (GTBD), a very comprehensive and well-structured database.
  * [Taxonomy labels](https://data.ace.uq.edu.au/public/gtdb/data/releases/release220/220.0/bac120_taxonomy_r220.tsv.gz): 
  * [Full genomes](https://data.ace.uq.edu.au/public/gtdb/data/releases/release220/220.0/genomic_files_reps/gtdb_genomes_reps_r220.tar.gz) (at least a representative genome for each species or maybe strain)
  * [Subset of marker genes, aligned in an MSA](https://data.ace.uq.edu.au/public/gtdb/data/releases/release220/220.0/genomic_files_reps/bac120_msa_marker_genes_reps_r220.tar.gz") -- maybe one could use this as a much smaller set of genes per genome to play with.
  
  
  

