# Hidden Markov Model Nanopore Sequencing


Background: Nanopore sequencing is a technique where a DNA sequence passes through a tiny pore, generating electrical signals that can be used to identify the DNA sequence. The process works as follows:

DNA Sequence Processing:

A DNA sequence is split into overlapping k-mers (k=5)

Example: ACGTAC → [ACGTA, CGTAC]

Each k-mer has a characteristic baseline signal level

Signal Generation Process:


As DNA moves through the pore:

Each k-mer stays in the pore for a random duration

While in the pore, it generates Gaussian noise around its baseline level

The DNA can move forward or backward, so next k-mer can be either the next or previous one

Multiple reads are generated for the same DNA sequence

Data Provided:


Training Data (train_data.pkl):


sequence: The original DNA sequence

kmers: List of all k-mers from the sequence

baseline_levels: Expected signal level for each k-mer

simulations: 1000 reads, each containing:

raw_signal: Time series of electrical signals

states: True k-mer indices generating each signal

Reference Data:



kmer_baseline_table.tsv: Mean and std of signal levels for each possible k-mer

Test Data:



test_data_raw_signals.npy: 100 signal sequences from the same DNA

Model Parameters:



Transition: A k-mer can only move to adjacent k-mers (previous/next)

Emission: Gaussian distribution around k-mer's baseline

All k-mers have the same transition probabilities

Tasks:

Turn this Nanopore Sequencing problem into a HMM model. Write down your model in the form of equations.

Infer the transition probabilities and the emission distribution parameters (baseline level and standard deviation) using the training data. Report the difference 

between the inferred and the true parameters. You can use sklearn.hmm.GaussianHMM for this task.

Predict the DNA sequence corresponding to the test data test_data_raw_signals.npy, which contains a list of 100 raw signals corresponding to the same DNA sequence.

Try to implement the Forward-Backward algorithm to infer the most likely path of the states from scratch. Do you get the same result as sklearn?

Could you design a RNN or Transformer model for this task?
