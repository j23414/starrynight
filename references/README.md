# ICTV References

[Exemplar Isolates of Viral Species](https://ictv.global/taxonomy/taxondetails?taxnode_id=202507214&taxon_name=Stellavirales)

```bash
export INPUT=sequences.fasta
export REFERENCE=reference.fna

makeblastdb -in ${REFERENCE} -dbtype nucl 

blastn \
    -db ${REFERENCE} \
    -query $INPUT \
    -outfmt 6 \
    -num_alignments 5 \
    -out blast_out.txt

# awk commands to pull out accession,blast_cluster top hit
# add a step to prune out any results that do not have enough coverage or identity
# spike in this information via the ingest/defaults/annotations.tsv
```