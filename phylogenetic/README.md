# Phylogenetic

```bash
# In production, use "nextflow run j23414/augment ..."
# But since augment is under active development, run the local copy here
nextflow run ~/github/j23414/augment/main.nf \
--newick data/Astrovirus.WGS.ALL.aln.FastTree.nwk \
--metadata ../ingest/results/metadata.tsv \
--metadata_id_columns "accession_version"  \
--metadata_annotate "strain date region country host host_category host_genus host_class host_order host_family host_broad_group is_lab_host note organism group blast_species major_cluster minor_cluster" \
--metadata_color_order defaults/color_orderings.tsv \
--metadata_set_colors defaults/host_broad_group_colors.tsv \
--export_args "--geo-resolutions region country " \
--alignment data/Astrovirus.WGS.ALL.aln \
--refine_args "--timetree --keep-polytomies" \
--outdir results_wgs \
-resume

nextflow run ~/github/j23414/augment/main.nf \
--newick data/AstV-ORF2.WGS.ALL.aln.FastTree.nwk \
--metadata ../ingest/results/metadata.tsv \
--metadata_id_columns "accession_version"  \
--metadata_annotate "strain date region country host host_category host_genus host_class host_order host_family host_broad_group is_lab_host note organism group cluster blast_species major_cluster minor_cluster" \
--metadata_color_order defaults/color_orderings.tsv \
--export_args "--geo-resolutions region country " \
--alignment data/AstV-ORF2.WGS.ALL.aln \
--refine_args "--timetree --keep-polytomies" \
--outdir results_orf2 \
-resume

nextflow run ~/github/j23414/augment/main.nf \
--newick data/AstV-ORF1b.WGS.ALL.aln.FastTree.nwk \
--metadata ../ingest/results/metadata.tsv \
--metadata_id_columns "accession_version"  \
--metadata_annotate "strain date region country host host_category host_genus host_class host_order host_family host_broad_group is_lab_host note organism group cluster blast_species major_cluster minor_cluster" \
--metadata_color_order defaults/color_orderings.tsv \
--export_args "--geo-resolutions region country " \
--alignment data/AstV-ORF1b.WGS.ALL.aln \
--refine_args "--timetree --keep-polytomies" \
--outdir results_orf1b \
-resume
```

Build major-cluster-based trees for better alignment and gene annotations, and to evaluate minor-clusters:

```bash
nextflow run ~/github/j23414/augment/main.nf \
--newick data/tree45.tre \
--metadata ../ingest/results/metadata.tsv \
--metadata_id_columns "accession_version"  \
--metadata_annotate "strain date region country host host_category host_genus host_class host_order host_family host_broad_group is_lab_host note organism group blast_species major_cluster minor_cluster" \
--metadata_color_order defaults/color_orderings.tsv \
--metadata_set_colors defaults/host_broad_group_colors.tsv \
--export_args "--geo-resolutions region country " \
--alignment data/AStV-SC-45.dedup.final.aln \
--refine_args "--timetree --keep-polytomies" \
--outdir results_45tree \
-resume

nextflow run ~/github/j23414/augment/main.nf \
--newick data/tree3.tre \
--metadata ../ingest/results/metadata.tsv \
--metadata_id_columns "accession_version"  \
--metadata_annotate "strain date region country host host_category host_genus host_class host_order host_family host_broad_group is_lab_host note organism group cluster blast_species major_cluster minor_cluster" \
--metadata_color_order defaults/color_orderings.tsv \
--metadata_set_colors defaults/host_broad_group_colors.tsv \
--export_args "--geo-resolutions region country " \
--alignment data/aln3.fna \
--refine_args "--timetree --keep-polytomies" \
--outdir results_3tree \
-resume
```
