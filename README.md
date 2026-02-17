Computational Multi-Omics Systems Biology of Bovine Mastitis Susceptibility in Dairy Cattle
Pilot analysis abandoned February 2026

Project Goal
Identify novel host-pathogen transcriptional networks and biomarkers for subclinical mastitis (SCM) resilience in Holstein dairy cattle using PRJNA390595 (1,400+ cows, udder/blood RNA-seq + 50k SNPs). Target: genomic selection for resilient breeding stock amid AMR threats (Staph aureus, E coli, Mycoplasma).
Key gap addressed: Bridge phenotype-genotype via WGCNA on SCM quarters → SNP colocalisation.

Datasets
    • Primary: NCBI BioProject PRJNA390595 (Holstein SCM cases/controls; Illumina RNA-seq udder somatic cells; Illumina BovineSNP50 BeadChip)
    • ​Secondary: ARS-USDA mastitis QTLdb, 1000 Bull Genomes
    • Pilot subset: n=16 quarters (8 healthy, 8 SCM) for de novo Trinity/HISAT2 benchmarking

Methods Pipeline (Abandoned State)

1. Data: fasterq-dump → FastQC/MultiQC
2. Dual alignment:
   a) Trinity de novo → HISAT2 contigs → idxstats (3,404 → 425 features)
   b) HISAT2 ARS-UCD1.2 → featureCounts (Option A, unimplemented)
3. WGCNA (R 4.4): β=12 (scale-free R²=0.90), 5 modules
4. ME5 resilience signature: r=-0.58 vs SCM (P=0.044 raw, fragile)
5. Hub annotation: BLASTX nr (Feb 2026) → Table S4b

Outputs (data/mastitis_project/):
text
├── wgcna_objects.RData          # datExpr, MEs, moduleColors (n=16)
├── signedKME.csv               # Top hubs kME≥0.999 (fill blanks!)
├── Table_S4b.png               # 55% transposon/olfactory artifacts
├── sample_dendrogram.png       # QC: no outliers
└── scale_free_plot.png         # β=12 optimal

Key Findings (Why Abandoned)
ME5 transcriptional signature preserved direction when scaled n=9→16 (r=-0.58, P_adj=?). Fatal flaw: MEturquoise hubs dominated by assembly artifacts:
    • 55% repeats/LINEs (ranks 6-7), olfactory GPCRs (ranks 3,8)
    • True candidates: Zinc finger OZF (rank 1, kME=1.0), ubiquitin hydrolase 17 (rank 4)
Root cause: ARS-UCD2.0 Hereford unplaced scaffolds misassemble transposons as high-variance 'hubs'. De novo Trinity exacerbates; genome-guided (featureCounts) needed but untested.
Table S4b Summary:
Issue	% Hubs	Example
Artifacts	55%	LINE RT (830 score), Olfr1175-like
Candidates	45%	Zinc OZF (99%ID), hornerin-like

Lessons Learned
    1. Never WGCNA de novo assemblies in bovine udder RNA-seq—repeats poison hubs
    2. n ≥15 minimum but P-values fragile without correction
    3. Option A essential: HISAT2 ARS-UCD1.2 + Ensembl GTF → ~3k clean genes
    4. PRJNA390595 goldmine but needs SNP metadata curation for n=100+ GWAS

Future Work (Not Pursued)
    1. Genome-guided WGCNA (n=16→50) → clean ME5
    2. GWAS colocalisation: 50k SNPs → breeding QTLs (BTA6/13/20?)
    3. Austrian Red Holstein validation (local data)

Why Abandoned
Epistemic modesty: 55% artifact hubs + fragile statistics = no biological discovery. Hypothesis-generating at best, but risks misleading field. Archive for others—future studies can salvage Zinc OZF + SNP integration. No publication attempted.
Citation

McCulloch, CR (2026). Abandoned pilot: WGCNA reveals de novo assembly failure in bovine mastitis RNA-seq.
GitHub: Cameron-99/mastitis_project (Accessed [date]).
DOI: 10.5281/zenodo.[future]
License & Reuse
MIT. Fork freely. Critical: Implement Option A before scaling.
Contact: vet19@gmx.at
Last run: 2026-02-17 (LMDE7, i5-7500, 16GB RAM)

Status: Negative controls teach most. This pipeline exposes why bovine multi-omics lags. Use responsibly.
