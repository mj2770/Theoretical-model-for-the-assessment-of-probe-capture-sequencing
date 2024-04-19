
---
# Sequencing modeling

---
* Date: 3/7/24
* Author: Minxi
* Final Version: 2.0

---
## Description: 

This model quantitatively assesses the sequencing results from hybrid probe-capture-based sequencing of human viruses from wastewater samples.

The inputs consist of several assumed characteristics of the total RNA after extraction using any selected concentration and extraction method. Under the iterated initial human virus/non-human virus mass ratio,the output results compare the preformance of different sequencing panels regarding the relative abundance of total targeted viruses, the relative abundance of one virus included in all panels (SARS-CoV-2), and the required minimal sequencing depth to detect this virus with the highest probability. In the meantime, this model also calculates the detection probability of different viruses under varied defined detection thresholds.

Overall, this quantitative model allowes for a theoretical assessment of the performance of probe-capture sequencing using different panels, and emphasizes the essential pre-sequencing factors in extracted total nucleic acids, which might be used as generalized indicators for the sequencing success, regardless of selected concentration/extraction methods and varied wastewater conditions.

---
## Assumptions:

  * **Assumptions of initial condition in the extracted RNA**:

    * A total of 5000 human RNA viruses could be presented in the extracted RNA, including SARS-CoV-2 and Mamastrovirus, the rest background including non-human viruses (bacteriphages + plant viruses), bacteria, archaea, human cells etc..
    * Human viruses were categorized by low, medium, and high abundances, each following a different normal distribution of intial gc and genome length (see below for details of the distribution).
    * SARS-CoV-2 has an initial gc of 5000 while Mamastrovirus has an initial gc of 50000.
    * The **mass ratio** refers to the total mass ratio of 5000 human RNA viruses to non-viral background in the extracted RNA (**ranging from 1E-8 to 1E-1**).
   
  ![Characteristics of 5000 virus strains in modeled extracted wastewater samples]

  * **Assumptions of the probe-capture sequencing**:

    * Different panels include probes targeting different subsets of the 5000 human viruses (see below for details). Those non-targeted viruses will be regarded as background
    * **Enrichment fold = 100X** (based on Rehn et al. 2021 paper). Different panels have the same enrichment fold of the targeted viruses included in the panel. Each virus or anything (maybe the false positive sequences) that matches the same probe should has the same enrichment fold regardless of its concentration in the sample.
    * **Depletion fold = 100X** (based on Rehn et al. 2021 paper). Different panels have the same depletion fold for the non-targeted background. However, it's important to note that this calculation is based on a single wastewater background composition, and different wastewater compositions may result in varying depletion ratios in reality.
    * After tagmentation, the **segment length = 500 bp**, and the final **reads length = 150 bp**.
    * The targeted virus strains have no sequence overlap or redundancy.
    
  * **Assumptions of virus coverage**: In Part 1 calculation, the defined **coverage breadth = 90%**, and the required **coverage depth = 10X**.

  * **Notes**: The values in the assumptions could be changed based on future research results, while this calculation model could still be adapted.
---
## Constants:

  * Molecular weight of RNA **MRNA = 321.5 Da/bp**
  * Da to nanogram conversion factor **Da_ng = 1.66 X 1E-15**
---
## Model structure:
![Model calculation equations](https://github.com/mj2770/Theoretical-model-for-the-assessment-of-probe-capture-sequencing/blob/main/Model%20structure-02.png)
