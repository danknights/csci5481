# Tips for research project
The research project is open-ended, and you are encouraged to be creative and follow your own interests. However, many students end up wanting to use common types of data and resources, so I have gathered frequently used advice and links here. They are organized according to the data type. This list is far from exhaustive; it is merely scratching the surface of what is available online.
  
### Data sources
* Raw shotgun data for assembly
  * Individual bacterial (or other) genomes
    * You can search the NCBI Sequence Read Archive (SRA)
      database for a particular organism: https://www.ncbi.nlm.nih.gov/sra. For example, if you search "Salmonella",
      you will find thousands of shotgun sequencing data sets. You can filter by technology, e.g. Illumina for
      short-read data. To download the raw sequencing data, click on the data set link, then click the link under "Run"
      at the bottom of the page, then click "FASTA/FASTQ download" at the top, then select "Filtered", then "FASTA.
      This will download the raw sequencing file. Note: When the data set is paired-end, even though you get
      one FASTA file, the forward and reverse reads are interleaved. You could treat them as single-end reads, but
      assembly will work better if you treat them as paired-end (because the assembler knows the two ends belonged to
      the same molecule). SPADES automatically can input interleaved DNA with the "--12" flag;
      see here: https://ablab.github.io/spades/running.html#input-data
  * Metagenomes (mixtures of genomes)
    * Deep shotgun metagenomics data from ~15 wild and ~15 captive Primates is available on MSI here: `/home/knightsd/public/pmp/shotgun`. The associated metadata, such as the primate species and the wild vs. captive status are in the `map.txt` file.
    * Ultra-ultra deep human metagenomics data (~2.5b paired-end reads, about 1.5TB per sample for 2 samples) are available on my CS network storage (note to self: /project/flatiron/data/uds). By request, I can move these over to the temporary "scratch" storage on MSI.
    * Raw data can be found for most published metagenomic data sets on SRA or EBI MGnify. The best way is probably to start with a publication in which you are interested, and find out where the data are deposited, usually in a section near the end called "Data Availability". Or you can go straight to the databases and search for projects. On SRA you can search for a "BioProject" with metagenomic samples, for example with [this query](https://www.ncbi.nlm.nih.gov/bioproject/?term=(%22human%20gut%20metagenome%22)%20AND%20bioproject_sra[filter]). On EBI MGnify, you can start at the [home page](https://www.ebi.ac.uk/metagenomics), click _Browse data_ > _Studies_, then enter "metagenomics" or "metagenome" in the _Filter_ field. In some cases you may not be able to find the necessary metadata (experimental variables) associated with the samples, in which case you will need to find the publication and search for a metadata table either in the supplementary materials or as a link in the Data Availability section. Be prepared for this to require non-trivial effort; acquiring and formatting published data is often one of the hardest parts. Tip: if you are having trouble finding good data sets on a particular topic (e.g. colorectal cancer), try to find a well-cited meta-analysis or review paper, and follow their citations.

