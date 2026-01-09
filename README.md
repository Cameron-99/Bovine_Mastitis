# BETSE-Controlled Bioelectric Goal States
**Bioelectricity 2026** | ODE→BETSE Extension

**Results:** HCN2_somite 1.20→0.30→1.18 (93% recovery)

## Reproduce Figures (90s):
```
cd src/somite_sim
# Drug: python3 -c "...HCN2=0.3..." && betse seed && betse sim && betse plot sim sim_config/sim_config.yml
# Recover: python3 -c "...HCN2=1.18..." && betse seed && betse sim && betse plot sim sim_config/sim_config.yml  
```
# betse-paper2-
