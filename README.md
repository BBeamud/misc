# Misc

Commands for tools and custom scripts used in manuscript

## 1. Genome analyses of bacteriophages 

### Databases

**[inphared](https://github.com/RyanCook94/inphared)**

Get up-to-date bacteriophage genome database

`perl523 inphared.pl`

*PS: Only worked with perl version 5.23 for me* 

**[seqtk](https://github.com/lh3/seqtk)**

Get *Klebsiella* phages from inphared



### Quality control

**[FASTQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/)**

` fastqc . `

**[prinseq](http://prinseq.sourceforge.net/)**

` prinseq . `

### Assembly

**[Unicycler](https://github.com/rrwick/Unicycler)** (v.)

` unicycler`

**[SPADES](http://cab.spbu.ru/software/spades/)** (v.) 

` spades.py `

**[MIRA4](https://sourceforge.net/p/mira-assembler/wiki/Home/)** (v.)

*You might have to downsample your data (<100x)

## Assembly quality

**[QUAST](https://github.com/ablab/quast)** (v.)

Basic stats

`quast.py`

**[apc](https://github.com/tseemann/apc/blob/master/apc.pl)**

Check circulariry of phage genomes

`perl apc.pl -b $output -r $sample_join_corrected.fastq $genome.fasta`

*PS: Corrected reads were obtained from SPAdes assembly and concatenated with 'cat'. 

### Annotation

**[PROKKA](https://github.com/tseemann/prokka)**

`prokka `

**[InterProScan](https://www.ebi.ac.uk/interpro/download/)**
`interproscan`

**[HMMER](

**[hmmscan]

### Comparative genomics

**[fastANI](https://github.com/ParBLiSS/FastANI)**

To discriminate between phage strains within isolated phages:

`fastANI --ql $list_fasta_new.txt --rl $list_fasta_new.txt -o $output.txt --fragLen 50 --matrix`

To compare phages against previously sequenced:

`fastANI --ql $list_fasta_new_ref.txt --rl $list_fasta_new_ref.txt -o $output.txt --fragLen 500 --matrix`

Get ref sequences which are related to your phages:


**[VIRIDIC](http://rhea.icbm.uni-oldenburg.de/VIRIDIC/)**

To obtain intergenomic similarities to classifiy phages into genera:

`viridic.bash projdir=$output_dir in=$`

*PS: In order to run VIRIDIC successfully with a large number of genomes you might have to modify the options of the **[future](https://github.com/HenrikBengtsson/future)** R package in your Rprofile: options(future.globals.maxSize=600000000) (that size worked for me)*

**[ViPTreeGen](https://github.com/yosuken/ViPTreeGen)**

To compare phages against *Klebsiella* viruses.

`ViPTreeGen --ncpus 8 $new_ref_kleb.fasta $output`

*PS: You have to make sure that your seq ids are short*

### Depolymerases 


### Recombination


### Prepare genbank submission


### Plots
