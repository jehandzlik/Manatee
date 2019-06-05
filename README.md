# Manatee
Manatee version 1.0

## What is Manatee?

	Manatee is a tool for detection, quantification and analysis of small ncRNAs 
	from next-generation sequencing data.
	
### DEPENDENCIES
1.	perl
2.	Set::IntervalTree: perl package
3.	SAMtools: need to be installed and added to your PATH
4.	Bowtie: executable file included in Manatee package, no installation required

### INSTALLATION (Unix/Linux)

Install the required dependencies and execute Manatee main script as described in the usage section. 

#### Set::IntervalTree

`cpan`

`install Set::IntervalTree`
	

### PACKAGE FILES
The following compontents are included in the Manatee package. 

    bowtie-1.0.1       % directory with bowtie aligner

    config             % configuration file

    Manatee            % Perl core program for sRNA analysis
    
    README.md          % this file

    trans-index        % directory where the transcriptome index will be stored


### USAGE with configuration file

###### Syntax:
`Manatee -config <file> -i <file> -o <dir>`

<table><tr><td>

    -config <file>

</td><td>
	
Path to configuration file.

</td></tr><tr><td>

    -i  <file>
    
</td><td>
	
Path to pre-processed FASTQ or FASTA file. Valid formats: .fa, .fasta, .fastq, .fq, .fa.gz,
                       .fasta.gz, .fastq.gz, .fq.gz.

</td></tr><tr><td>

    -o <dir>

</td><td>
	
Path to directory where the output will be stored.

</td></tr>

</table>

	

### USAGE with input parameters

###### Syntax:
`Manatee [OPTIONS] -i <file> -o <dir> -index <ebwt> -genome <file> -annotation <file>`

<table>
<tr><td>

    -i <file>

</td><td>
	
Path to pre-processed FASTQ or FASTA file. Valid formats: .fa, .fasta, .fastq, .fq, .fa.gz,
                       .fasta.gz, .fastq.gz, .fq.gz.

</td></tr><tr><td>

    -o <dir>

</td><td>
	
Path to directory where the output will be stored.

</td></tr><tr><td>

    -index <ebwt>

</td><td>
	
Path and basename of the genome index to be searched. The basename is the name of any of the index files up to but not including the final .1.ebwt/.rev.1.ebwt/etc. 

</td></tr><tr><td>

    -genome <file>

</td><td>
	
Path to genome FA or FASTA file. 

</td></tr><tr><td>

    -annotation <file>

</td><td>
	
Path to non coding annotation file. File should contain the following tab seperated elements: chromosome, strand, start loci, end loci, biotype, transcript id, transcript name.

</td></tr>
</table>

### OPTIONS

<table>

<tr><td>

    -t_index <ebwt>

</td><td>

Path and basename of the transcriptome index to be searched. The basename is the name of any of the index files up to but not including the final .1.ebwt/.rev.1.ebwt/etc. If left blank, in case of non existing index, Manatee will generate transcriptome index based on the provided non coding annotation and will store that index within the transcripts directory.
</td></tr><tr><td>

    -cores <int>

</td><td>

Number of alignment cores (default: -cores 1).

</td></tr><tr><td>

    -collapse <yes/no>

</td><td>

Collapse reads with the same genomic sequences. This setting reduces significantly the execution time. Possible values ues/no (default: -collapse yes).


</td></tr><tr><td>

    -m <int>

</td><td>

Max of multimapping loci, -m in bowtie execution. The mapping algorithm will be 
applied only for reads with multi-mapped loci less or equal than -m. Reads with 
multimapped loci that exceed the m will be aligned against transcriptome 
(default: m=50).


</td></tr><tr><td>

    -mismatches <int> 

</td><td>

Maximun number of mismatches in genomic alignments (default: mismatches=1).

</td></tr><tr><td>

    -m <int>

</td><td>

Max of multimapping loci, -m in bowtie execution. The mapping algorithm will be applied only for reads with multi-mapped loci less or equal than m. Reads with multimapped loci that exceed the -m will be aligned against transcriptome (default: -m 200).

</td></tr><tr><td>

    -s <yes/no>

</td><td>

Strand specific mode of the algorithm (default -strand_mode yes).

</td></tr><tr><td>

    -cd <int>

</td><td>

Minimum number of unannotated read abundances per cluster (default: -cd 5).

</td></tr><tr><td>

    -cdi <int>

</td><td>

Clusters of unannotated reads will be merged if the distance between them is equal or less than cdi (default: -cdi 50).

</td></tr>


</table>
