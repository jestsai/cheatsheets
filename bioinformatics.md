# Bioinformatics

This is a cheat sheet for bioinformatics command line programs.

## HOMER motif finding

Use [HOMER](http://homer.salk.edu/homer/ngs/peakMotifs.html) for finding motifs in the genome given bed files.

### For RNA

Build a command using Python

```python
# Search for short motifs, lenghts 4,5,6,7 with up to 1 mismatch
n_processors = 4
homer_flags = '-rna -len 4,5,6,7 -mset vertebrates -mis 1 -p {}'.format(n_processors)
findMotifsGenome = '/home/yeo-lab/software/homer/bin/findMotifsGenome.pl'
command = '{} {} hg19 {} -bg {} {}'.format(
        findMotifsGenome, bedfile, out_dir, background, homer_flags)
```
 
The final command looks like this:

```
findMotifsGenome.pl peaks.bed out_dir hg19 -bg background.bed -rna -len 4,5,6,7 -mset vertebrates -mis 1 -p 4
```

## Create sequence reference dictionary

Using Picard tools

```
picard CreateSequenceDictionary\
R = .fasta\
O = .dict\
```
