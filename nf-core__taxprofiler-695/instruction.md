# Issue

**Title:** Add nf-test: test_alternativepreprocessing

## Description

Directory structure to check:

```tree
results_altpreprocessing/
├── adapterremoval
│   ├── 2612_ERR5766176_B.settings
│   ├── 2612_ERR5766176.settings
│   └── 2613_ERR5766181.settings
├── bbduk
│   ├── 2612_ERR5766176_B.bbduk.log
│   ├── 2612_ERR5766176.bbduk.log
│   └── 2613_ERR5766181.bbduk.log
├── bowtie2
│   └── align
│       ├── 2612_ERR5766176_B.bowtie2.log
│       ├── 2612_ERR5766176.bowtie2.log
│       └── 2613_ERR5766181.bowtie2.log
├── fastqc
│   ├── processed
│   │   ├── 2612_ERR5766176_B_processed_1_fastqc.html
│   │   ├── 2612_ERR5766176_B_processed_1_fastqc.zip
│   │   ├── 2612_ERR5766176_B_processed_2_fastqc.html
│   │   ├── 2612_ERR5766176_B_processed_2_fastqc.zip
│   │   ├── 2612_ERR5766176_processed_1_fastqc.html
│   │   ├── 2612_ERR5766176_processed_1_fastqc.zip
│   │   ├── 2612_ERR5766176_processed_2_fastqc.html
│   │   ├── 2612_ERR5766176_processed_2_fastqc.zip
│   │   ├── 2613_ERR5766181_processed_1_fastqc.html
│   │   ├── 2613_ERR5766181_processed_1_fastqc.zip
│   │   ├── 2613_ERR5766181_processed_2_fastqc.html
│   │   ├── 2613_ERR5766181_processed_2_fastqc.zip
│   │   ├── ERR3201952_ERR3201952_processed_fastqc.html
│   │   └── ERR3201952_ERR3201952_processed_fastqc.zip
│   └── raw
│       ├── 2612_ERR5766176_B_raw_1_fastqc.html
│       ├── 2612_ERR5766176_B_raw_1_fastqc.zip
│       ├── 2612_ERR5766176_B_raw_2_fastqc.html
│       ├── 2612_ERR5766176_B_raw_2_fastqc.zip
│       ├── 2612_ERR5766176_raw_1_fastqc.html
│       ├── 2612_ERR5766176_raw_1_fastqc.zip
│       ├── 2612_ERR5766176_raw_2_fastqc.html
│       ├── 2612_ERR5766176_raw_2_fastqc.zip
│       ├── 2613_ERR5766181_raw_1_fastqc.html
│       ├── 2613_ERR5766181_raw_1_fastqc.zip
│       ├── 2613_ERR5766181_raw_2_fastqc.html
│       ├── 2613_ERR5766181_raw_2_fastqc.zip
│       ├── ERR3201952_ERR3201952_raw_fastqc.html
│       └── ERR3201952_ERR3201952_raw_fastqc.zip
├── filtlong
│   └── ERR3201952_ERR3201952_filtered.log
├── kaiju
│   ├── db5
│   │   ├── 2611_db5.kaijutable.txt
│   │   ├── 2611_db5.kaiju.tsv
│   │   ├── 2612_db5.kaijutable.txt
│   │   ├── 2612_db5.kaiju.tsv
│   │   ├── 2613_db5.kaijutable.txt
│   │   └── 2613_db5.kaiju.tsv
│   ├── db6
│   │   ├── 2614_db6.kaijutable.txt
│   │   ├── 2614_db6.kaiju.tsv
│   │   ├── ERR3201952_db6.kaijutable.txt
│   │   └── ERR3201952_db6.kaiju.tsv
│   └── db7
│       ├── 2611_db7.kaijutable.txt
│       ├── 2611_db7.kaiju.tsv
│       ├── 2612_db7.kaijutable.txt
│       ├── 2612_db7.kaiju.tsv
│       ├── 2613_db7.kaijutable.txt
│       ├── 2613_db7.kaiju.tsv
│       ├── 2614_db7.kaijutable.txt
│       ├── 2614_db7.kaiju.tsv
│       ├── ERR3201952_db7.kaijutable.txt
│       └── ERR3201952_db7.kaiju.tsv
├── kraken2
│   └── db2
│       ├── 2611_db2.kraken2.kraken2.report.txt
│       ├── 2612_db2.kraken2.kraken2.report.txt
│       └── 2613_db2.kraken2.kraken2.report.txt
├── multiqc
│   ├── multiqc_data
│   │   ├── ar_length_count_plot_All.txt
│   │   ├── ar_length_count_plot_Discarded.txt
│   │   ├── ar_length_count_plot_Mate1.txt
│   │   ├── ar_length_count_plot_Mate2.txt
│   │   ├── ar_length_count_plot_Singleton.txt
│   │   ├── ar_retained_plot.txt
│   │   ├── bbduk-filtered-barplot_Bases.txt
│   │   ├── bbduk-filtered-barplot_Reads.txt
│   │   ├── bbduk.txt
│   │   ├── bowtie2_pe_plot.txt
│   │   ├── fastqc-1_adapter_content_plot.txt
│   │   ├── fastqc-1_per_base_n_content_plot.txt
│   │   ├── fastqc-1_per_base_sequence_quality_plot.txt
│   │   ├── fastqc-1_per_sequence_gc_content_plot_Counts.txt
│   │   ├── fastqc-1_per_sequence_gc_content_plot_Percentages.txt
│   │   ├── fastqc-1_per_sequence_quality_scores_plot.txt
│   │   ├── fastqc-1_sequence_counts_plot.txt
│   │   ├── fastqc-1_sequence_duplication_levels_plot.txt
│   │   ├── fastqc-1-status-check-heatmap.txt
│   │   ├── fastqc_adapter_content_plot.txt
│   │   ├── fastqc_per_base_n_content_plot.txt
│   │   ├── fastqc_per_base_sequence_quality_plot.txt
│   │   ├── fastqc_per_sequence_gc_content_plot_Counts.txt
│   │   ├── fastqc_per_sequence_gc_content_plot_Percentages.txt
│   │   ├── fastqc_per_sequence_quality_scores_plot.txt
│   │   ├── fastqc_sequence_counts_plot.txt
│   │   ├── fastqc_sequence_duplication_levels_plot.txt
│   │   ├── fastqc_sequence_length_distribution_plot.txt
│   │   ├── fastqc-status-check-heatmap.txt
│   │   ├── filtlong.txt
│   │   ├── kaiju-topfive-plot.txt
│   │   ├── kraken-top-n-plot_Class.txt
│   │   ├── kraken-top-n-plot_Domain.txt
│   │   ├── kraken-top-n-plot_Family.txt
│   │   ├── kraken-top-n-plot_Genus.txt
│   │   ├── kraken-top-n-plot_Kingdom.txt
│   │   ├── kraken-top-n-plot_Order.txt
│   │   ├── kraken-top-n-plot_Phylum.txt
│   │   ├── kraken-top-n-plot_Species.txt
│   │   ├── kraken-top-n-plot_Unclassified.txt
│   │   ├── llms-full.txt
│   │   ├── multiqc_adapter_removal.txt
│   │   ├── multiqc_bowtie2.txt
│   │   ├── multiqc_citations.txt
│   │   ├── multiqc_data.json
│   │   ├── multiqc_fastqc_fastqc-1.txt
│   │   ├── multiqc_fastqc.txt
│   │   ├── multiqc_general_stats.txt
│   │   ├── multiqc_kaiju_species.txt
│   │   ├── multiqc_kraken.txt
│   │   ├── multiqc.log
│   │   ├── multiqc.parquet
│   │   ├── multiqc_samtools_stats.txt
│   │   ├── multiqc_software_versions.txt
│   │   ├── multiqc_sources.txt
│   │   ├── porechop-endtrim-barplot.txt
│   │   ├── porechop-middlesplit-barplot.txt
│   │   ├── porechop_porechop.txt
│   │   ├── porechop-starttrim-barplot.txt
│   │   ├── samtools_alignment_plot.txt
│   │   └── samtools-stats-dp.txt
│   ├── multiqc_plots
│   │   ├── pdf
│   │   │   ├── ar_length_count_plot_All.pdf
│   │   │   ├── ar_length_count_plot_Discarded.pdf
│   │   │   ├── ar_length_count_plot_Mate1.pdf
│   │   │   ├── ar_length_count_plot_Mate2.pdf
│   │   │   ├── ar_length_count_plot_Singleton.pdf
│   │   │   ├── ar_retained_plot-cnt.pdf
│   │   │   ├── ar_retained_plot-pct.pdf
│   │   │   ├── bbduk-filtered-barplot_Bases-cnt.pdf
│   │   │   ├── bbduk-filtered-barplot_Bases-pct.pdf
│   │   │   ├── bbduk-filtered-barplot_Reads-cnt.pdf
│   │   │   ├── bbduk-filtered-barplot_Reads-pct.pdf
│   │   │   ├── bowtie2_pe_plot-cnt.pdf
│   │   │   ├── bowtie2_pe_plot-pct.pdf
│   │   │   ├── fastqc-1_adapter_content_plot.pdf
│   │   │   ├── fastqc-1_per_base_n_content_plot.pdf
│   │   │   ├── fastqc-1_per_base_sequence_quality_plot.pdf
│   │   │   ├── fastqc-1_per_sequence_gc_content_plot_Counts.pdf
│   │   │   ├── fastqc-1_per_sequence_gc_content_plot_Percentages.pdf
│   │   │   ├── fastqc-1_per_sequence_quality_scores_plot.pdf
│   │   │   ├── fastqc-1_sequence_counts_plot-cnt.pdf
│   │   │   ├── fastqc-1_sequence_counts_plot-pct.pdf
│   │   │   ├── fastqc-1_sequence_duplication_levels_plot.pdf
│   │   │   ├── fastqc_adapter_content_plot.pdf
│   │   │   ├── fastqc_per_base_n_content_plot.pdf
│   │   │   ├── fastqc_per_base_sequence_quality_plot.pdf
│   │   │   ├── fastqc_per_sequence_gc_content_plot_Counts.pdf
│   │   │   ├── fastqc_per_sequence_gc_content_plot_Percentages.pdf
│   │   │   ├── fastqc_per_sequence_quality_scores_plot.pdf
│   │   │   ├── fastqc_sequence_counts_plot-cnt.pdf
│   │   │   ├── fastqc_sequence_counts_plot-pct.pdf
│   │   │   ├── fastqc_sequence_duplication_levels_plot.pdf
│   │   │   ├── fastqc_sequence_length_distribution_plot.pdf
│   │   │   ├── kaiju-topfive-plot-cnt.pdf
│   │   │   ├── kaiju-topfive-plot-pct.pdf
│   │   │   ├── kraken-top-n-plot_Class-cnt.pdf
│   │   │   ├── kraken-top-n-plot_Class-pct.pdf
│   │   │   ├── kraken-top-n-plot_Domain-cnt.pdf
│   │   │   ├── kraken-top-n-plot_Domain-pct.pdf
│   │   │   ├── kraken-top-n-plot_Family-cnt.pdf
│   │   │   ├── kraken-top-n-plot_Family-pct.pdf
│   │   │   ├── kraken-top-n-plot_Genus-cnt.pdf
│   │   │   ├── kraken-top-n-plot_Genus-pct.pdf
│   │   │   ├── kraken-top-n-plot_Kingdom-cnt.pdf
│   │   │   ├── kraken-top-n-plot_Kingdom-pct.pdf
│   │   │   ├── kraken-top-n-plot_Order-cnt.pdf
│   │   │   ├── kraken-top-n-plot_Order-pct.pdf
│   │   │   ├── kraken-top-n-plot_Phylum-cnt.pdf
│   │   │   ├── kraken-top-n-plot_Phylum-pct.pdf
│   │   │   ├── kraken-top-n-plot_Species-cnt.pdf
│   │   │   ├── kraken-top-n-plot_Species-pct.pdf
│   │   │   ├── kraken-top-n-plot_Unclassified-cnt.pdf
│   │   │   ├── kraken-top-n-plot_Unclassified-pct.pdf
│   │   │   ├── porechop-endtrim-barplot-cnt.pdf
│   │   │   ├── porechop-endtrim-barplot-pct.pdf
│   │   │   ├── porechop-middlesplit-barplot-cnt.pdf
│   │   │   ├── porechop-middlesplit-barplot-pct.pdf
│   │   │   ├── porechop-starttrim-barplot-cnt.pdf
│   │   │   ├── porechop-starttrim-barplot-pct.pdf
│   │   │   ├── samtools_alignment_plot-cnt.pdf
│   │   │   ├── samtools_alignment_plot-pct.pdf
│   │   │   └── samtools-stats-dp.pdf
│   │   ├── png
│   │   │   ├── ar_length_count_plot_All.png
│   │   │   ├── ar_length_count_plot_Discarded.png
│   │   │   ├── ar_length_count_plot_Mate1.png
│   │   │   ├── ar_length_count_plot_Mate2.png
│   │   │   ├── ar_length_count_plot_Singleton.png
│   │   │   ├── ar_retained_plot-cnt.png
│   │   │   ├── ar_retained_plot-pct.png
│   │   │   ├── bbduk-filtered-barplot_Bases-cnt.png
│   │   │   ├── bbduk-filtered-barplot_Bases-pct.png
│   │   │   ├── bbduk-filtered-barplot_Reads-cnt.png
│   │   │   ├── bbduk-filtered-barplot_Reads-pct.png
│   │   │   ├── bowtie2_pe_plot-cnt.png
│   │   │   ├── bowtie2_pe_plot-pct.png
│   │   │   ├── fastqc-1_adapter_content_plot.png
│   │   │   ├── fastqc-1_per_base_n_content_plot.png
│   │   │   ├── fastqc-1_per_base_sequence_quality_plot.png
│   │   │   ├── fastqc-1_per_sequence_gc_content_plot_Counts.png
│   │   │   ├── fastqc-1_per_sequence_gc_content_plot_Percentages.png
│   │   │   ├── fastqc-1_per_sequence_quality_scores_plot.png
│   │   │   ├── fastqc-1_sequence_counts_plot-cnt.png
│   │   │   ├── fastqc-1_sequence_counts_plot-pct.png
│   │   │   ├── fastqc-1_sequence_duplication_levels_plot.png
│   │   │   ├── fastqc_adapter_content_plot.png
│   │   │   ├── fastqc_per_base_n_content_plot.png
│   │   │   ├── fastqc_per_base_sequence_quality_plot.png
│   │   │   ├── fastqc_per_sequence_gc_content_plot_Counts.png
│   │   │   ├── fastqc_per_sequence_gc_content_plot_Percentages.png
│   │   │   ├── fastqc_per_sequence_quality_scores_plot.png
│   │   │   ├── fastqc_sequence_counts_plot-cnt.png
│   │   │   ├── fastqc_sequence_counts_plot-pct.png
│   │   │   ├── fastqc_sequence_duplication_levels_plot.png
│   │   │   ├── fastqc_sequence_length_distribution_plot.png
│   │   │   ├── kaiju-topfive-plot-cnt.png
│   │   │   ├── kaiju-topfive-plot-pct.png
│   │   │   ├── kraken-top-n-plot_Class-cnt.png
│   │   │   ├── kraken-top-n-plot_Class-pct.png
│   │   │   ├── kraken-top-n-plot_Domain-cnt.png
│   │   │   ├── kraken-top-n-plot_Domain-pct.png
│   │   │   ├── kraken-top-n-plot_Family-cnt.png
│   │   │   ├── kraken-top-n-plot_Family-pct.png
│   │   │   ├── kraken-top-n-plot_Genus-cnt.png
│   │   │   ├── kraken-top-n-plot_Genus-pct.png
│   │   │   ├── kraken-top-n-plot_Kingdom-cnt.png
│   │   │   ├── kraken-top-n-plot_Kingdom-pct.png
│   │   │   ├── kraken-top-n-plot_Order-cnt.png
│   │   │   ├── kraken-top-n-plot_Order-pct.png
│   │   │   ├── kraken-top-n-plot_Phylum-cnt.png
│   │   │   ├── kraken-top-n-plot_Phylum-pct.png
│   │   │   ├── kraken-top-n-plot_Species-cnt.png
│   │   │   ├── kraken-top-n-plot_Species-pct.png
│   │   │   ├── kraken-top-n-plot_Unclassified-cnt.png
│   │   │   ├── kraken-top-n-plot_Unclassified-pct.png
│   │   │   ├── porechop-endtrim-barplot-cnt.png
│   │   │   ├── porechop-endtrim-barplot-pct.png
│   │   │   ├── porechop-middlesplit-barplot-cnt.png
│   │   │   ├── porechop-middlesplit-barplot-pct.png
│   │   │   ├── porechop-starttrim-barplot-cnt.png
│   │   │   ├── porechop-starttrim-barplot-pct.png
│   │   │   ├── samtools_alignment_plot-cnt.png
│   │   │   ├── samtools_alignment_plot-pct.png
│   │   │   └── samtools-stats-dp.png
│   │   └── svg
│   │       ├── ar_length_count_plot_All.svg
│   │       ├── ar_length_count_plot_Discarded.svg
│   │       ├── ar_length_count_plot_Mate1.svg
│   │       ├── ar_length_count_plot_Mate2.svg
│   │       ├── ar_length_count_plot_Singleton.svg
│   │       ├── ar_retained_plot-cnt.svg
│   │       ├── ar_retained_plot-pct.svg
│   │       ├── bbduk-filtered-barplot_Bases-cnt.svg
│   │       ├── bbduk-filtered-barplot_Bases-pct.svg
│   │       ├── bbduk-filtered-barplot_Reads-cnt.svg
│   │       ├── bbduk-filtered-barplot_Reads-pct.svg
│   │       ├── bowtie2_pe_plot-cnt.svg
│   │       ├── bowtie2_pe_plot-pct.svg
│   │       ├── fastqc-1_adapter_content_plot.svg
│   │       ├── fastqc-1_per_base_n_content_plot.svg
│   │       ├── fastqc-1_per_base_sequence_quality_plot.svg
│   │       ├── fastqc-1_per_sequence_gc_content_plot_Counts.svg
│   │       ├── fastqc-1_per_sequence_gc_content_plot_Percentages.svg
│   │       ├── fastqc-1_per_sequence_quality_scores_plot.svg
│   │       ├── fastqc-1_sequence_counts_plot-cnt.svg
│   │       ├── fastqc-1_sequence_counts_plot-pct.svg
│   │       ├── fastqc-1_sequence_duplication_levels_plot.svg
│   │       ├── fastqc_adapter_content_plot.svg
│   │       ├── fastqc_per_base_n_content_plot.svg
│   │       ├── fastqc_per_base_sequence_quality_plot.svg
│   │       ├── fastqc_per_sequence_gc_content_plot_Counts.svg
│   │       ├── fastqc_per_sequence_gc_content_plot_Percentages.svg
│   │       ├── fastqc_per_sequence_quality_scores_plot.svg
│   │       ├── fastqc_sequence_counts_plot-cnt.svg
│   │       ├── fastqc_sequence_counts_plot-pct.svg
│   │       ├── fastqc_sequence_duplication_levels_plot.svg
│   │       ├── fastqc_sequence_length_distribution_plot.svg
│   │       ├── kaiju-topfive-plot-cnt.svg
│   │       ├── kaiju-topfive-plot-pct.svg
│   │       ├── kraken-top-n-plot_Class-cnt.svg
│   │       ├── kraken-top-n-plot_Class-pct.svg
│   │       ├── kraken-top-n-plot_Domain-cnt.svg
│   │       ├── kraken-top-n-plot_Domain-pct.svg
│   │       ├── kraken-top-n-plot_Family-cnt.svg
│   │       ├── kraken-top-n-plot_Family-pct.svg
│   │       ├── kraken-top-n-plot_Genus-cnt.svg
│   │       ├── kraken-top-n-plot_Genus-pct.svg
│   │       ├── kraken-top-n-plot_Kingdom-cnt.svg
│   │       ├── kraken-top-n-plot_Kingdom-pct.svg
│   │       ├── kraken-top-n-plot_Order-cnt.svg
│   │       ├── kraken-top-n-plot_Order-pct.svg
│   │       ├── kraken-top-n-plot_Phylum-cnt.svg
│   │       ├── kraken-top-n-plot_Phylum-pct.svg
│   │       ├── kraken-top-n-plot_Species-cnt.svg
│   │       ├── kraken-top-n-plot_Species-pct.svg
│   │       ├── kraken-top-n-plot_Unclassified-cnt.svg
│   │       ├── kraken-top-n-plot_Unclassified-pct.svg
│   │       ├── porechop-endtrim-barplot-cnt.svg
│   │       ├── porechop-endtrim-barplot-pct.svg
│   │       ├── porechop-middlesplit-barplot-cnt.svg
│   │       ├── porechop-middlesplit-barplot-pct.svg
│   │       ├── porechop-starttrim-barplot-cnt.svg
│   │       ├── porechop-starttrim-barplot-pct.svg
│   │       ├── samtools_alignment_plot-cnt.svg
│   │       ├── samtools_alignment_plot-pct.svg
│   │       └── samtools-stats-dp.svg
│   └── multiqc_report.html
├── pipeline_info
│   ├── execution_report_2026-03-01_13-15-35.html
│   ├── execution_report_2026-03-01_13-24-00.html
│   ├── execution_report_2026-03-01_13-26-31.html
│   ├── execution_report_2026-03-01_13-28-50.html
│   ├── execution_report_2026-03-01_13-32-27.html
│   ├── execution_report_2026-03-01_13-35-51.html
│   ├── execution_report_2026-03-01_13-38-01.html
│   ├── execution_report_2026-03-01_13-40-19.html
│   ├── execution_report_2026-03-01_13-40-55.html
│   ├── execution_timeline_2026-03-01_13-15-35.html
│   ├── execution_timeline_2026-03-01_13-24-00.html
│   ├── execution_timeline_2026-03-01_13-26-31.html
│   ├── execution_timeline_2026-03-01_13-28-50.html
│   ├── execution_timeline_2026-03-01_13-32-27.html
│   ├── execution_timeline_2026-03-01_13-35-51.html
│   ├── execution_timeline_2026-03-01_13-38-01.html
│   ├── execution_timeline_2026-03-01_13-40-19.html
│   ├── execution_timeline_2026-03-01_13-40-55.html
│   ├── execution_trace_2026-03-01_13-15-35.txt
│   ├── execution_trace_2026-03-01_13-24-00.txt
│   ├── execution_trace_2026-03-01_13-26-31.txt
│   ├── execution_trace_2026-03-01_13-28-50.txt
│   ├── execution_trace_2026-03-01_13-32-27.txt
│   ├── execution_trace_2026-03-01_13-35-51.txt
│   ├── execution_trace_2026-03-01_13-38-01.txt
│   ├── execution_trace_2026-03-01_13-40-19.txt
│   ├── execution_trace_2026-03-01_13-40-55.txt
│   ├── nf_core_taxprofiler_software_mqc_versions.yml
│   ├── params_2026-03-01_13-15-46.json
│   ├── params_2026-03-01_13-24-11.json
│   ├── params_2026-03-01_13-26-42.json
│   ├── params_2026-03-01_13-29-01.json
│   ├── params_2026-03-01_13-32-37.json
│   ├── params_2026-03-01_13-36-01.json
│   ├── params_2026-03-01_13-38-12.json
│   ├── params_2026-03-01_13-40-31.json
│   ├── params_2026-03-01_13-41-04.json
│   ├── pipeline_dag_2026-03-01_13-15-35.html
│   ├── pipeline_dag_2026-03-01_13-24-00.html
│   ├── pipeline_dag_2026-03-01_13-26-31.html
│   ├── pipeline_dag_2026-03-01_13-28-50.html
│   ├── pipeline_dag_2026-03-01_13-32-27.html
│   ├── pipeline_dag_2026-03-01_13-35-51.html
│   ├── pipeline_dag_2026-03-01_13-38-01.html
│   ├── pipeline_dag_2026-03-01_13-40-19.html
│   └── pipeline_dag_2026-03-01_13-40-55.html
├── porechop
│   └── ERR3201952_ERR3201952_porechop.log
└── samtools
    └── stats
        ├── 2612_ERR5766176_B.stats
        ├── 2612_ERR5766176.stats
        ├── 2613_ERR5766181.stats
        └── ERR3201952_ERR3201952.stats
```

## PR checklist

- [ ] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/taxprofiler/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/taxprofiler _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `48453a4b74fa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.