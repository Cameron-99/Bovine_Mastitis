
Bovine_Mastitis/
├── README.md                 # Pipeline overview, results summary, figure links
├── Snakefile                 # Complete workflow (download→align→quantify→WGCNA)
├── environment.yml           # Conda env (HISAT2, samtools, R 4.4.1, WGCNA)
├── config.yaml               # Sample metadata (n=16 SRA accessions, SCM status)
├── 01_wgcna_analysis.R      # Core WGCNA script (β=12, 6 modules, MEturquoise)
├── 02_module_validation.R   # Dendrogram, scale-free fit, Holm correction
├── table1_modules.tsv       # 6 modules (3-1783 contigs) 
├── table2_correlations.tsv  # MEturquoise r=-0.87, Holm P=6.2×10⁻⁵
└── figure1_dendrogram.png   # n=16 sample clustering (9H:7SCM)

# Bovine Mastitis Resilience Networks (PRJNA390595 n=16)

**Contig-level WGCNA** identifies MEturquoise (1783 contigs, r=-0.87 SCM) bypassing Ensembl annotation bias.

## Results
- 6 modules (Table 1)
- MEturquoise strongest resilience signal (Table 2)
- Scale-free R²=0.92 (power=12)

## Reproduce
```bash
conda env create -f environment.yml
snakemake --cores 4
Rscript 01_wgcna_analysis.R
