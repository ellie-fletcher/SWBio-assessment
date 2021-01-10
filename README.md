# SWBio-assessment: Python assessment for Data Science and Machine Learning

This is a pipeline written in Python to produce a list of 'high-scoring' candidates proposed to interact with a protein of interest. A co-immunoprecipitation experiment (using a GFP-tagged version of a protein of interest) followed by Liquid Chromatography Mass Spectrometry carried out by the Proteomics Facility (University of Bristol) generated the data for this code. Data returned by the Proteomics Facility can be large (thousands of potential interactors) and involves multiple Excel spreadsheets. This code enables efficient tidying, filtering, analysing and sorting of data to reveal the 'highest-scoring' interactors for further analysis, which can then be exported. This code features an extension to retrieve information on a candidate from NCBI after finding the protein sequence (FASTA file format) via the exported, ordered Accession numbers. 

1. Download the Python notebook entitled 'EFassessment_code.ipynb' and the sample data entitled 'Made_up_data_2.xlsx'. The extension requires the FASTA file 'Q8LPJ4.fasta.txt' to be downloaded. All files should be downloaded into a single directory.

2. Run steps 1-5 to:
...1. Read in data
...2. Tidy the data
...3. Filter for the columns needed for the analysis
...4. Remove candidates with low (<4) PSM values (Peptide Spectrum Matches- the total number of identified peptide sequences for the protein i.e. the number of times the protein was identified in the sample) in the GFP-MRF line. 
...5. Create a new column containing the ratio of PSM values GFP-MRF/Col0 i.e.	the fold increase in presence of the candidate in the pull-down (GFP-MRF) compared to the WT (Col0).

3. Run step 6 to filter for high-scoring candidates:
Step 6 requires a judgement on the number of candidates you would like to investigate balanced by concerns about false positives. Some researchers will deem a candidate interesting if it has a PSM ratio value of 2 (2-fold increase in prescence compared to the WT PSM value), however this may yield false positives and could return more candidates than you would have time to investigate. Here, a value of 5 is used which is stringent but could remove interesting candidates. The suggested range is between 2 and 5. 

4. Run steps 7-10:
        7. Order the candidates
        8. Retrieve NaN PSM ratio value candidates
        9. Merge the ordered PSM ratio value and NaN PSM ratio value datasets
        10. Export the final dataset
