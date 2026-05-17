# Hidden Markov Model and Viterbi Algorithm

This repository contains an implementation of a Hidden Markov Model (HMM) and the Viterbi Algorithm for decoding nucleotide sequences. The assignment focuses on identifying the most probable hidden state sequence corresponding to a DNA query sequence.

## Files


* `Assignment_HMM_and_Viterbi_completed.ipynb`
  Fully completed implementation of the HMM and Viterbi decoding algorithm.

## Objective

The goal of this assignment is to:

1. Model nucleotide sequences using a Hidden Markov Model.
2. Compute probabilities of different hidden state paths.
3. Implement the Viterbi dynamic programming algorithm.
4. Reconstruct the most probable hidden state sequence using traceback.

## Hidden States

The HMM uses the following states:

| State | Meaning           |
| ----- | ----------------- |
| `s`   | Start state       |
| `E`   | Exon              |
| `5`   | Splice donor site |
| `I`   | Intron            |
| `e`   | End state         |

## Concepts Implemented

### Transition Probabilities

Defines the probability of moving from one hidden state to another.

### Emission Probabilities

Defines the probability of observing a nucleotide (`A`, `C`, `G`, `T`) from a hidden state.

### Log Probabilities

Logarithms are used instead of raw probabilities to avoid numerical underflow during multiplication of many small probabilities.

### Viterbi Algorithm

Dynamic programming approach used to compute the most probable hidden state path for the observed sequence.

### Traceback

After filling the Viterbi matrix, traceback is performed to reconstruct the optimal hidden state sequence.

## Main Components

### 1. Probability Calculation

The notebook first evaluates manually defined state paths and computes their log probabilities.

Function used:

```python
get_log_prob_for_state_path(state_path, query_sequence)
```

### 2. Viterbi Matrix Construction

Two matrices are initialized:

* `viterbi_value_matrix`

  * Stores maximum log probabilities.

* `viterbi_trace_matrix`

  * Stores traceback information for reconstructing paths.

### 3. Node Probability Computation

Each Viterbi cell is computed using:

```python
calculate_prob_for_a_node(row, col)
```

This function:

* evaluates all possible previous states,
* computes transition + emission probabilities,
* selects the maximum probability path.

### 4. Traceback

Final hidden state sequence reconstruction:

```python
traceback_state_path()
```

## Example Query Sequence

```python
CTTCATGTGAAAGCAGACGTAAGTCA
```

## Technologies Used

* Python
* NumPy
* Jupyter Notebook

## How to Run

1. Install dependencies:

```bash
pip install numpy jupyter
```

2. Launch Jupyter Notebook:

```bash
jupyter notebook
```

3. Open:

```text
Assignment_HMM_and_Viterbi_completed.ipynb
```

4. Run all cells sequentially.
