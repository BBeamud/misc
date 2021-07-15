# Misc

Commands for tools and custom scripts used in manuscript with tips & tricks 

## 1. Genome analyses of bacteriophages 

### Databases

**[inphared](https://github.com/RyanCook94/inphared)**

Get up-to-date bacteriophage genome database

`perl523 inphared.pl`

*PS: Only worked with perl version 5.23 for me. Ryan is always willing to help with issues, so don't be afraid to reach him, it is worthy!* 

**[seqtk](https://github.com/lh3/seqtk)**

Get *Klebsiella* phages from inphared



### Quality control

**[FASTQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/)**

` fastqc . `

**[prinseq](http://prinseq.sourceforge.net/)**

` prinseq . `

### Assembly

We prioritised **Unicycler** over the rest of programs as we observed more consistent results for technical replicates and closely-related strains. Plus: you have also the info about the circularisation of the genome. If Unicycler does not success, 'the more you try, the better'. 

**[Unicycler](https://github.com/rrwick/Unicycler)** (v.)

` unicycler`

**[SPAdes](http://cab.spbu.ru/software/spades/)** (v.) 

` spades.py `

**[MIRA4](https://sourceforge.net/p/mira-assembler/wiki/Home/)** (v.)

Max. k-mer size for SPAdes (and therefore, Unicycler) is 127. That's almost in the limit for 150 bp reads, but for 250 bp, the increase of the k-mer size can aid a lot (in our experience) to close phage genomes at the cost of increased computation time. 

Using a template of the manifest file [MIRA_manifest_ex.txt]( ) with custom parameters (k-mer sizes of 149,171 & 193)

`cat MIRA_manifest_ex.txt | sed "s/SAMPLE/$d/" | sed "s/R1/$R1/" | sed "s/R2/$R2/" > mira-$d-manifest.txt
mira mira-$d-manifest.txt`

*You might have to downsample your data (<100x)*

## Assembly quality

**[QUAST](https://github.com/ablab/quast)** (v.)

Basic stats

`quast.py`

**[apc](https://github.com/tseemann/apc/blob/master/apc.pl)**

Check circulariry of phage genomes

`perl apc.pl -b $output -r $sample_join_corrected.fastq $genome.fasta`

*PS: Corrected reads were obtained from SPAdes assembly and concatenated with 'cat'* 

### Annotation

**[PROKKA](https://github.com/tseemann/prokka)**

`prokka `

*PS: Even you used a database with prokka to improve annotations, prokka by default seems to take the name of the first hit only. If the first hit is annotated as an hypothetical protein you'll miss the rest of the info*. 

**[BLASTP]()**




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

**[InterProScan](https://www.ebi.ac.uk/interpro/download/)**
`interproscan`

**[HMMER](

### Recombination


### Prepare genbank submission


### Plots
