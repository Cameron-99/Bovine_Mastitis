
Bovine Mastitis WGCNA Analysis (PRJNA390595)

Weighted Gene Co-expression Network Analysis identifies ME5 resilience biomarker in Holstein milk somatic cell RNA-seq (n=9; 94% HISAT2 mapping)
🎯 Project Summary

WGCNA of PRJNA390595 milk somatic cell transcriptomes (4 healthy, 5 subclinical mastitis Holstein quarters) identifies ME5 (383 genes, r=-0.565, P=0.044) as candidate transcriptional biomarker for mastitis resilience. Addresses €2B annual EU/US losses through genomic selection targets. Publication-ready pipeline (48 CPU-hours, i5-7500/16GB Linux LMDE 7).

Status: Veterinary Research manuscript complete (1 Fig, 2 Tables, GitHub supplements)

Bovine_Mastitis/
├── data/
│   ├── raw/          # SRR24593469-77 FASTQs (~1TB)
│   ├── processed/    # 400×9 expression matrix
│   └── metadata/     # SCC phenotypes
├── analysis/
│   ├── 01_hisat2.sh  # HISAT2 alignment (94% mapping)
│   ├── 02_wgcna.R    # Ward.D2 clustering → 5 modules
│   └── 03_david.R    # ME5 enrichment (TLR q=0.012)
├── results/
│   ├── fig1_dendrogram.tiff  # 600dpi publication
│   ├── table1_pipeline.csv
│   └── table2_me_correlations.csv
├── manuscript/
│   └── First-draft.pdf     # Current version
└── README.md

Quich Start (Linux)
# 1. Clone (fork first!)
git clone https://github.com/Cameron-99/Bovine_Mastitis.git
cd Bovine_Mastitis

# 2. Download SRA data (1TB)
mkdir -p data/raw
cd data/raw
fasterq-dump SRR24593469:SRR24593477 --split-files --threads 4

# 3. Run pipeline
bash analysis/01_hisat2.sh    # 94% mapping
Rscript analysis/02_wgcna.R   # ME5 discovery
Rscript analysis/03_david.R   # Validation

Linux LMDE 7 (i5-7500, 16GB)
HISAT2 v2.2.1, samtools v1.15, R v4.3.2
WGCNA v1.70, DAVID v6.8

Citation
Cameron-99/Bovine_Mastitis (2026) Weighted Gene Co-expression Network Analysis 
Identifies Protective Modules in Subclinical Bovine Mastitis. 
github.com/Cameron-99/Bovine_Mastitis (Accessed 2026-02-03)

Veterinarians/breeders: ME5 enables genomic selection for mastitis resilience. Contact for collaboration. Email: vet19@gmx.at
