# AbInitioProteinStr

# Group 2: Ab Initio Protein Secondary Structure Prediction

**Date:** 12th December, 2024  
**Members:** Arth Banka, Riti Bhatia, Sanchitha Kuthethoor, Sumeet Kothare  
**Demo Link:** [Project Demo](https://drive.google.com/file/d/1X8fdxQFILHfyiLvSTlYzYjZ6NzGQ1mI8/view?usp=drive_link)  

## Project Motivation
Protein secondary structure prediction is a fundamental problem in computational biology. In this project, we explored early heuristic-based methods for predicting secondary structures from amino acid sequences. Our focus was on implementing and analyzing classical algorithms, including **Chou-Fasman**, **GOR**, and a **Hidden Markov Model (HMM)**. Instead of using modern deep-learning-based methods like AlphaFold2, we aimed to understand and evaluate the performance of these earlier models in predicting secondary structures such as **alpha helices, beta sheets, turns, and coils**.

## Computational Problem
The goal of this project was to develop a computational pipeline that, given an amino acid sequence, outputs a corresponding secondary structure sequence. The prediction accuracy was evaluated against **DSSP**-derived experimental secondary structures. Our models were designed to be lightweight, using minimal computational resources and classical probabilistic and statistical approaches instead of large-scale deep learning.

## Folder Structure
```
AbInitioPS/
├── Figures/
│   ├── Miscellaneous ".png" files
├── GOR_InfoVals/
│   ├── InfoVal_aHelix.csv
│   ├── InfoVal_bStrand.csv
│   ├── InfoVal_bTurn.csv
│   ├── InfoVal_Coil.csv
├── GORTests/
│   ├── GORPredict/
│   │   ├── Input/
│   │   ├── Output/
│   ├── SlideWindow/
│       ├── Input/
│       ├── Output/
├── .RData
├── .Rhistory
├── AccuracyTestDataset_50.csv
├── AppUI.R
├── auto_Validation.R
├── CF_functions_test.go
├── CF_functions.go
├── datatypes.go
├── EM_main.go
├── GOR_functions_test.go
├── GOR_functions.go
├── hmm_functions_test.go
├── HMM_functions.go
├── main.go
├── README.md
```

## Description of Files
- **CF_functions.go**: Implements the Chou-Fasman algorithm.
- **CF_functions_test.go**: Unit tests for Chou-Fasman functions.
- **datatypes.go**: Defines shared data types.
- **EM_main.go**: Implements Expectation-Maximization for HMM training.
- **GOR_functions.go**: Implements the GOR algorithm.
- **GOR_functions_test.go**: Unit tests for GOR method.
- **HMM_functions.go**: Implements the Hidden Markov Model for structure prediction.
- **hmm_functions_test.go**: Unit tests for HMM implementation.
- **main.go**: Main entry point, integrating all models.
- **AppUI.R**: RShiny application for sequence input and visualization.
- **auto_Validation.R**: RShiny tool for validating model predictions.
- **AccuracyTestDataset_50.csv**: Dataset used for model validation.

## Building and Running the Go Code
### Prerequisites
- **Go (1.18 or higher)**
- **Operating System:** macOS or Windows

### Build Instructions
```
cd path/to/AbInitioPS
# Compile the main Go program
go build -o ProteinPredictor main.go
```

### Run the Code
#### macOS/Linux:
```
./ProteinPredictor "ETGTVPAINYLGAGYDHVRGNPVGDPSSMGDPGIRPPVLRF"
```
#### Windows:
```
ProteinPredictor.exe "ETGTVPAINYLGAGYDHVRGNPVGDPSSMGDPGIRPPVLRF"
```

### Running Tests
```
go test ./...
```
For testing specific modules:
```
go test -v CF_functions_test.go
```

## Running the R Shiny Applications
### Prerequisites
- **R (Version 4.1 or higher)**
- **RShiny package installed:** `install.packages("shiny")`
- **Additional Libraries:** `ggplot2`, `reshape2`

### Run AppUI.R
1. Open **RStudio**.
2. Load `AppUI.R`.
3. Click **Run App**.
4. Use the interface to:
   - Enter a protein sequence or upload a FASTA file.
   - Select Chou-Fasman, GOR, or HMM models.
   - View predicted structures and comparison graphs.

### Run auto_Validation.R
1. Open **RStudio**.
2. Load `auto_Validation.R`.
3. Click **Run App**.
4. Upload a CSV file containing:
   - `ProteinName`
   - `ProteinSequence`
   - `DSSPSequence`
5. Outputs include:
   - Per-protein accuracy.
   - Model-wise performance metrics.
   - Graphical comparisons of precision, recall, and F1-score.

## Overview of Algorithms
### Chou-Fasman Algorithm
A sliding window-based method that assigns **propensity scores** to amino acids, identifying helix and sheet nucleation sites. Overlapping predictions are resolved based on higher propensity values.

### Garnier-Osguthorpe-Robson (GOR) Algorithm
Uses **information theory** to evaluate each amino acid's likelihood of forming a secondary structure based on **neighboring residues**. Employs probability tables derived from known protein structures.

### Hidden Markov Model (HMM)
Models protein structures as **hidden states** in a Markov chain. **Viterbi decoding** is used to determine the most likely sequence of secondary structures based on trained **transition and emission probabilities**.

## Model Performance and Validation
### Accuracy
- **Chou-Fasman:** 35.02%
- **GOR:** 41.19%
- **HMM:** 47.29%

### Evaluation Metrics
- **Precision, Recall, and F1-Score** calculated for **Helices (H), Beta Sheets (E), Turns (T), and Coils (C)**.
- **HMM showed highest accuracy**, but **GOR had lower variance** in predictions.
- **Turns were least accurately predicted** across all models.

## Contributions
- **Arth Banka:** HMM research, implementation, and testing.
- **Riti Bhatia:** Chou-Fasman implementation and testing.
- **Sanchitha Kuthethoor:** RShiny UI development and model validation.
- **Sumeet Kothare:** GOR implementation and visualizations.

## References
1. Chou, P. Y., & Fasman, G. D. (1978). Empirical predictions of protein conformation.
2. Garnier, J., Osguthorpe, D. J., & Robson, B. (1978). Statistical prediction of secondary structures.
3. Ding et al. (2012). PRT-HMM: A Novel Hidden Markov Model for Protein Secondary Structure Prediction.
4. Kabsch, W., & Sander, C. (1983). DSSP: Dictionary of Protein Secondary Structure.
5. McDonough, M. (2024). Did AI solve the protein-folding problem? Harvard Medicine Magazine.

This README provides an in-depth overview of our project, its methodologies, and execution details. 🚀

