# RNA-Seq_Profiling
RNA-Seq Equivalence Class Profiling and Alignment Using k-mer Analysis

Sure! Here’s a README file for your code:

---

# RNA-Seq Equivalence Class Profiling and Alignment Using k-mer Analysis

This program performs RNA-Seq expression profiling by analyzing k-mers from RNA-Seq reads and comparing them to k-mers from a reference transcriptome. It identifies equivalence classes of reads, counts the number of reads mapping to each equivalence class, and visualizes the results.

## Table of Contents
1. [Requirements](#requirements)
2. [Usage](#usage)
3. [Code Overview](#code-overview)
4. [Output](#output)

## Requirements

The following Python packages are required:
- pandas
- numpy
- matplotlib
- tabulate

Additionally, the following tools should be installed:
- FastQC
- Trimmomatic
- HISAT2
- SAMtools
- featureCounts (subread package)

To install the required Python packages, you can use:
```bash
pip install pandas numpy matplotlib tabulate
```

## Usage

1. **Prepare the input files:**
   - `chr11_transcriptome.fasta`: Reference transcriptome file in FASTA format.
   - `reads.fasta.gz`: RNA-Seq reads in gzipped FASTA format.

2. **Run the code:**
   ```python
   # Save the code into a file named rna_seq_profiling.py and run it
   python rna_seq_profiling.py
   ```

## Code Overview

### Imports
The code starts with importing necessary libraries:
```python
import pandas as pd
import numpy as np
import math
import random
from matplotlib import pyplot as plt
```

### Functions to Process k-mers
- **Canonical k-mer:** Computes the lexicographically smaller k-mer between the k-mer and its reverse complement.
- **Reverse Complement:** Computes the reverse complement of a given k-mer.

### Building the Hash Table from the Reference Transcriptome
Reads the reference transcriptome FASTA file, generates 31-mers, computes their canonical forms, and stores them in a hash table with their corresponding gene IDs.

### Generate k-mers and Equivalence Classes
- **Generate k-mers:** Generates all k-mers of a given length from a read and returns their canonical forms.
- **Get Equivalence Classes:** Determines the equivalence classes of a read by generating its k-mers and finding the intersection of their equivalence classes.

### Process RNA-Seq Reads
Reads RNA-Seq reads from a gzipped FASTA file, generates k-mers, determines equivalence classes, and counts how many reads map to each equivalence class.

### Display and Export Equivalence Class Counts
Displays the first 5 equivalence classes and their counts in a tabular format and exports the sorted equivalence class counts to a CSV file.

### Plot Equivalence Class Sizes
Plots the sizes of equivalence classes against the number of reads mapping to them, once including and once excluding the null set.

## Output

The program produces the following outputs:
- **Console Output:** 
  - Number of unique equivalence classes.
  - Table displaying the first 5 equivalence classes and their counts.
- **CSV File:** 
  - `my_dict.csv` containing sorted equivalence class counts.
- **Plots:** 
  - Bar plots showing the sizes of equivalence classes against the number of reads mapping to them.
