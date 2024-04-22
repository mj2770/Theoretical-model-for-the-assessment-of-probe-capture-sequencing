
---
# Sequencing modeling

---
* Date: 3/7/24
* Author: Minxi 
* Final Version: 2.0
* Acknowledgement: Special thanks to Rose Kantor for her contributions to discussing the model and assisting with editing all descriptions.

---
## Goals:
This model quantitatively simulates and compares sequencing results from different probe-capture enrichment panels for a modeled set of human viruses from wastewater samples.
This model also emphasizes the essential pre-sequencing factors in extracted total nucleic acids, which might be used as generalized indicators for the sequencing success, regardless of selected concentration/extraction methods and varied wastewater conditions.

---
  * **Assumptions of the probe-capture sequencing**:

    * **Enrichment fold** = 100X (based on Rehn et al. 2021).
      Different panels have the same enrichment fold of targeted viruses.
      Each virus has the same enrichment fold regardless of its concentration in the sample.
    * **Depletion fold** = 100X (based on Rehn et al. 2021). 
    * **Segment length** after tagmentation = 500 bp
    * **Read length** = 150 bp
    * There are 5000 unique virus strains in wastewater, which have no sequence overlap or redundancy.
    * **Mass ratio** of 5000 human RNA viruses to the non-viral background in the extracted RNA ranges from 1E-8 to 1E-1
    * Genome lengths of human virus strains are normally distributed (mean = 15000 bp, SD = 5000 bp), Absolute abundances (gene copies; “gc”) of human virus strains follow 3 normal distributions:
         * Low abundance: 20% of all virus strains (mean = 500 gc, SD = 143 gc)
         * Medium abundance: 60 % of all virus strains (mean = 10000 gc, SD = 2857 gc)
         * High abundance: 20% of all virus strains (mean = 25000 gc, SD = 7143 gc)

    * **Note**: These values may vary by probe panel and wastewater background sequence composition, which could be changed based on future research results.
---

## Model Initiation:

* Define 5000 human RNA viruses
   * Randomly assign the absolute abundance (genome copies) and genome length for 4998 viruses according to assumed distributions
   * Manually incorporate two viruses for comparison among different panels:
        * SARS-CoV-2: abundance = 5,000 gc, genome length = 30,000 bp
        * Mamastrovirus sp.: abundance = 50,000 gc, genome length = 7,000 bp
* Define the four different sequencing panels:
   * **Panel A**: Broad panel targeting 2,000 viruses (intended to represent respiratory, enteric, and other viruses). Panel includes SARS-CoV-2, Mamastrovirus sp., and 1,998 additional viruses randomly selected from the pool of 5000 viruses.
   * **Panel B**: Broad panel targeting 200 viruses (intended to represent respiratory, enteric, and other viruses). Panel includes SARS-CoV-2, Mamastrovirus sp., and 198 additional viruses randomly subset from the Panel A viruses.
   * **Panel C**: Narrow panel targeting 20 viruses (intended to represent respiratory viruses) including SARS-CoV-2 and 19 additional viruses with medium abundances randomly selected from the pool np.random.poisson(lam=100,60)
   * **Panel D**: Targeting only SARS-CoV-2 virus.
   
  ![Characteristics of 5000 virus strains in modeled extracted wastewater samples](https://github.com/mj2770/Theoretical-model-for-the-assessment-of-probe-capture-sequencing/blob/main/Distribution_3-02.png)

---
## Model Structure
---
### Constants:
  * Molecular weight of RNA **MRNA = 321.5 Da/bp**
  * Da to nanogram conversion factor **Da_ng = 1.66 X 1E-15**
### Model Calculation:
![Model calculation equations](https://github.com/mj2770/Theoretical-model-for-the-assessment-of-probe-capture-sequencing/blob/main/Model%20structure-02.png)
