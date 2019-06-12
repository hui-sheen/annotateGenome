# annotateGenome

This package is used to annotate bed file with pre-calculated genome information.

# installation

Install python main package:

```
pip install git+git://github.com/shengqh/annotateGenome.git
```

Install packages in R before you perform in comparison mode:

```
install.packages(c("optparse", "rmarkdown", "knitr", "MASS", "pscl"))

if (!requireNamespace("BiocManager", quietly = TRUE))
    install.packages("BiocManager")

BiocManager::install("GenomicRanges")
```

# required database (hg38)

Download **ALL** database files to same folder from:

https://cqsweb.app.vumc.org/download1/annotateGenome/hg38/

The database files include gzipped genome annotation for each chromosome (.gz), corresponding index file (.gz.tbi), range file (.bed) and chromosome length file (sizes.genome.txt).

```
wget https://cqsweb.app.vumc.org/download1/annotateGenome/hg38/file.list
wget -B https://cqsweb.app.vumc.org/download1/annotateGenome/hg38/ -i file.list
```

# example target files

You may download example target region files from:

https://cqsweb.app.vumc.org/download1/annotateGenome/examples/

```
wget https://cqsweb.app.vumc.org/download1/annotateGenome/examples/bed.list
wget -B https://cqsweb.app.vumc.org/download1/annotateGenome/examples/ -i bed.list
```

# usage

### Annotate one file (annotation mode)
```
annotateGenome -d folder_with_database -i bed_file -t
```
for example:
```
annotateGenome -d folder_with_database -i H3K27me3.bed -t
```

### Annotate and compare two files (comparison mode)
```
annotateGenome -d folder_with_database -i bed_file -c control_file
```

for example:
```
annotateGenome -d folder_with_database -i H3K27me3.bed -c H3K27ac.bed
```
