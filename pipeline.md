

Requirements: 

1. HapCUT2: https://github.com/vibansal/HapCUT2
2. SHAPEIT2: https://mathgen.stats.ox.ac.uk/genetics_software/shapeit/
3. 1000 Genomes reference panel haplotypes: https://mathgen.stats.ox.ac.uk/impute/1000GP_Phase3.html
4. BAM file and VCF file for individual to be phased 


Steps: 

1. Run extractHAIRS on the BAM and VCF file (see HapCUT2 instructions) 
2. Run SHAPEIT2 on the VCF file using the 1000 Genomes reference panel 
3. use encode.py to generate pseudo-reads 
4. combine the fragments from step (1) and (3) 
5. run HapCUT2 
