# Phylogenetic

```bash
nextflow run j23414/augment \
--newick data/Astrovirus.WGS.ALL.aln.FastTree.nwk \
--metadata ../ingest/results/metadata.tsv \
--metadata_id_columns "accession_version"  \
--metadata_annotate "strain date region country host host_category host_genus host_class host_order host_family host_broad_group is_lab_host note organism group blast_species" \
--metadata_color_order defaults/color_orderings.tsv \
--metadata_set_colors defaults/host_broad_group_colors.tsv \
--export_args "--geo-resolutions region country " \
--alignment data/Astrovirus.WGS.ALL.aln \
--refine_args "--timetree --keep-polytomies" \
--outdir results_wgs \
-resume

nextflow run j23414/augment \
--newick data/orf2_reordered.nwk \
--metadata ../ingest/results/metadata.tsv \
--metadata_id_columns "accession_version"  \
--metadata_annotate "strain date region country host host_category host_genus host_class host_order host_family host_broad_group is_lab_host note organism group blast_species" \
--metadata_color_order defaults/color_orderings.tsv \
--export_args "--geo-resolutions region country " \
--alignment data/AstV-ORF2.WGS.ALL.aln \
--refine_args "--keep-root" \
--outdir results_orf2 \
-resume
```
