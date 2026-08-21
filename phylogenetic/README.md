# Phylogenetic

```bash
# In production, use "nextflow run j23414/augment ..."
# But since augment is under active development, run the local copy here
nextflow run ~/github/j23414/augment/main.nf \
--conda_env "/Users/jchang99/.nextstrain/runtimes/conda/env" \
--newick data/Astrovirus.WGS.ALL.aln.FastTree.nwk \
--metadata data/metadata.tsv \
--metadata_id_columns "accession_version"  \
--metadata_annotate "strain date region country host host_category host_genus host_class host_order host_family host_broad_group is_lab_host note organism group blast_species cluster lineage" \
--metadata_color_order defaults/color_orderings.tsv \
--metadata_set_colors defaults/host_broad_group_colors.tsv \
--export_args "--geo-resolutions region country " \
--trait_columns "cluster region country" \
--alignment data/Astrovirus.WGS.ALL.aln \
--refine_args "--timetree --keep-polytomies" \
--reference_gb "defaults/ref.gb" \
--reference_fasta "defaults/ref.fasta" \
--outdir results_wgs \
--auspice_config_json "defaults/auspice_config.json" \
--description_md "defaults/description.md" \
-resume

nextflow run ~/github/j23414/augment/main.nf \
--newick data/AstV-ORF2.WGS.ALL.aln.FastTree.nwk \
--metadata data/metadata.tsv \
--metadata_id_columns "accession_version"  \
--metadata_annotate "strain date region country host host_category host_genus host_class host_order host_family host_broad_group is_lab_host note organism group cluster blast_species cluster lineage" \
--metadata_color_order defaults/color_orderings.tsv \
--export_args "--geo-resolutions region country " \
--alignment data/AstV-ORF2.WGS.ALL.aln \
--refine_args "--timetree --keep-polytomies" \
--outdir results_orf2 \
--auspice_config_json "defaults/auspice_config.json" \
--description_md "defaults/description.md" \
--conda_env "/Users/jchang99/.nextstrain/runtimes/conda/env" \
--trait_columns "cluster region country" \
-resume

nextflow run ~/github/j23414/augment/main.nf \
--newick data/AstV-ORF1b.WGS.ALL.aln.FastTree.nwk \
--metadata data/metadata.tsv \
--metadata_id_columns "accession_version"  \
--metadata_annotate "strain date region country host host_category host_genus host_class host_order host_family host_broad_group is_lab_host note organism group cluster blast_species cluster lineage" \
--metadata_color_order defaults/color_orderings.tsv \
--export_args "--geo-resolutions region country " \
--alignment data/AstV-ORF1b.WGS.ALL.aln \
--refine_args "--timetree --keep-polytomies" \
--outdir results_orf1b \
--auspice_config_json "defaults/auspice_config.json" \
--description_md "defaults/description.md" \
--conda_env "/Users/jchang99/.nextstrain/runtimes/conda/env" \
--trait_columns "cluster region country" \
-resume
```

Build major-cluster-based trees for better alignment and gene annotations, and to evaluate minor-clusters:

```bash
export NUM=2

nextflow run ~/github/j23414/augment/main.nf \
--newick data/aln/ALIGNMENTS/AStV-${NUM}.tre \
--metadata data/metadata.tsv \
--metadata_id_columns "accession_version"  \
--metadata_annotate "strain date region country host host_category host_genus host_class host_order host_family host_broad_group is_lab_host note organism group blast_species cluster lineage" \
--metadata_color_order defaults/color_orderings.tsv \
--metadata_set_colors defaults/host_broad_group_colors.tsv \
--export_args "--geo-resolutions region country " \
--alignment data/aln/ALIGNMENTS/AStV-${NUM}.db.aln \
--refine_args "--timetree --keep-polytomies" \
--trait_columns "cluster lineage region country" \
--outdir results_AStV_${NUM} \
--auspice_config_json "defaults/auspice_config.json" \
--description_md "defaults/description.md" \
--conda_env "/Users/jchang99/.nextstrain/runtimes/conda/env"
```