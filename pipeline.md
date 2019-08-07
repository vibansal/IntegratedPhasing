

Requirements: 

1. HapCUT2: https://github.com/vibansal/HapCUT2
2. SHAPEIT2: https://mathgen.stats.ox.ac.uk/genetics_software/shapeit/shapeit.html 
3. 1000 Genomes reference panel haplotypes: https://mathgen.stats.ox.ac.uk/impute/1000GP_Phase3.html
4. BAM file and VCF file for individual to be phased 


Steps: 

1. Run extractHAIRS on the BAM and VCF file  to obtain Hi-C fragments (see HapCUT2 instructions for how to do this, use option --hic 1)

2. Run SHAPEIT2 on the VCF file using the 1000 Genomes reference panel:

```
shapeit --input-vcf VCFfile -R reference_panel.hap reference_panel.legend reference_panel.samples -M genetic_map.txt --output-graph VCFfile.graph
```
The files reference_panel.hap, reference_panel.legend and reference_panel.samples (for each chromosome) can be downloaded from the link above. 

3. use samplehaps.py to sample 'N' haplotype pairs for the individual

```
python samplehaps.py VCFfile > VCFfile.haps
```

4. use encodereads.py to represent the haplotype samples as "pseudo-reads" 

5. concatenate the "Hi-C fragments" and the "pseudo-reads" to obtain the new "fragment file"

6. run HapCUT2 on the new "fragment file" to obtain phased haplotypes 
