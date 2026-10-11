# Experiment Design

### Experimental design principles

1. **Formulate the research question**
2. **Define Hypotheses**
3. **Identify of variables to measure**
    - Independent variables (the factor being manipulated)
    - Dependent variables (the observed outcome or response)
    - Control variables are factors held constant to prevent confounding effects
    - You may want to build a causal graph
4. **Power Analysis and Sample Size calculations**
    
    Conduct a power analysis to determine the sample size needed for the experiment to detect a meaningful effect. This helps ensure that the study has sufficient statistical power.
    
5. **Design Test and Control Groups**
6. **Randomization and/or Blocking**
    - Randomly assign participants to different experimental conditions. Randomization helps ensure that the groups are comparable at the start of the experiment, reducing the impact of confounding variables.
    - Implement blocking (grouping participants based on certain characteristics) and randomization within blocks to enhance the precision of estimates and control for potential confounding variables.
7. **Blinding**
    - Single-blind studies conceal information from participants
    - Double-blind studies extend this to both participants and experimenters.
8. **Statistical Analysis**
    
    Choose appropriate statistical methods to analyze the data. This may include t-tests, analysis of variance (ANOVA), regression analysis, and other inferential statistics.
    
9. **Documentation and Logging**
    
    Maintain detailed records of the experimental procedure, including any modifications made during the course of the study. Log relevant data point for post-experiment analysis
    
10. **Ethical Considerations**
    
    Adhere to ethical guidelines in the treatment of human or animal subjects. Obtain informed consent, minimize harm, and provide debriefing when necessary
    

### **Types of Experimental Designs**

**1.) Completely Randomized Design (CRD)**

**2.) Randomized Block Design (RBD)**

- Blocking: Experimental units are grouped into blocks based on some known characteristic that is expected to affect the response variable. The blocks are formed in such a way that units within a block are more similar to each other than to units in other blocks.
- Random assignment within blocks: After forming blocks, experimental units within each block are randomly assigned to different treatment groups

**3.) Factorial Design**

- Involves the simultaneous manipulation of two or more independent variables (factors) to study their individual and interactive effects on a dependent variable.
- In a 2x2 factorial design, there are two factors, and each factor has two levels.
- For example, if factor A represents type of treatment and has two levels (A1 and A2), and Factor B represents dosage with two levels (B1 and B2), the design would involve combinations like A1B1, A1B2, A2B1, and A2B2.
- Each combination of factor levels forms a **cell** in the design. Cells represent the unique treatment conditions. In a 2x2 design, there would be four cells.

**4.) Latin Square Design**

**5.) Split-Plot Design**

**6.) Repeated Measures Design**

The same subjects are used for each treatment or condition in the study. Unlike independent groups designs where different groups of participants are exposed to different conditions, repeated measures designs involve the same individuals being measured multiple times under different conditions

7.) **Matched Pair Design**

Matched-pair experiment is a design where each experimental unit is paired with another unit that is similar or matched in terms of relevant characteristics. One unit receives one treatment, while the matched unit receives a different treatment.

**8.) Switchback Design**

Switchback design involves assigning treatments to experimental units in a sequence, and then reversing the order of treatments in subsequent periods or blocks

### Randomization Techniques

1. **Simple Randomization:**
    - In simple randomization, each experimental unit has an equal chance of being assigned to any treatment group. This is typically done using random number generators or drawing lots.
2. **Stratified Randomization:**
    - Stratified randomization involves dividing the population into subgroups or strata based on certain characteristics (stratification variables) and then randomly assigning treatments within each stratum. This helps ensure that each subgroup is represented in each treatment group.
3. **Blocked Randomization:**
    - Blocking involves grouping experimental units into blocks based on specific characteristics that may influence the response variable. Within each block, randomization is then applied to assign units to different treatment groups.
4. **Cluster Sampling:**
    - Create clusters which are likely to have same or similar number of people from different subgroups. Select a subset of these clusters for a particular treatment and take all the members of the cluster for that treatment.

**Response Surface Methodology (RSM)**

([video](https://www.youtube.com/watch?v=ERSWvYybOrk))

- Optimization of response variables.
- Use of experimental designs to model complex relationships.

## Experimentation 201

**Source for table**: [https://www.youtube.com/watch?v=LOhvpOFAlf4](https://www.youtube.com/watch?v=LOhvpOFAlf4)

| **Limitation** | **Solution** |
| --- | --- |
| Experiments take too long | CUPED |
| Winner’s curse | Long-term holdouts |
| Peeking Problem | Sequential Testing |
| Bad randomization | Stratified sampling |
| Network effects | Switchback testing |
| Fixed allocation | Multi-arm bandits |
| No average user | Heterogenous treatment effects |