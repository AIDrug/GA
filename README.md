# Augmenting genetic algorithms with deep neural networks for exploring the chemical space
This repository contains code for the paper: [Augmenting genetic algorithms with deep neural networks for exploring the chemical space](https://arxiv.org/abs/1909.11655).
Here is a visualization of molecular progress: 

<img align="center" src="./readme_docs/mol_view.gif"/>

# Prerequisites

Before running the code, please ensure you have the following:


- [SELFIES (any version)](https://github.com/aspuru-guzik-group/selfies) - 
  The code was run with v0.1.1 (which is the fastest), however, the code is compatible with any version. 
- [RDKit](https://www.rdkit.org/docs/Install.html)
- [tensorboardX](https://pypi.org/project/tensorboardX/)
- [Pytorch v0.4.1](https://pytorch.org/)
- [Python 3.0 or up](https://www.python.org/download/releases/3.0/)
- [numpy](https://pypi.org/project/numpy/)


# How to run the code? : 
We highly recommend using the following version for running your experiments.  
```
python ./core_GA.py
```  

The following settings can be used (found at the end of the file): 
- num_generations: Number of generations to run the GA
- generation_size: Molecular population size encountered in each generation 
- starting_selfies: Initial population of molecules 
- max_molecules_len: Length of the largest molecule string
- disc_epochs_per_generation: Number of epochs of training the discriminator neural network 
- disc_enc_type: Type of molecular encoding shown to the discriminator
- disc_layers : Discriminator architecture
- training_start_gen: generation after which discriminator training begins 
- device: Device the discriminator is trained on 
- properties_calc_ls: Property evaluations to be completed for each molecule of the GA
- num_processors: Number of cpu cores to parallelize calculations over
- beta: Value of parameter beta
- impose_time_adapted_pen: Boolean variable to indicated use of a time-adapted discriminator penalty


# How are the results saved?  : 
All the results are savents in the 'results' directory. Our results are saved as (Note: 'i' is the run iteration): 
1. images_generation_0_i:  
   Images of the top 100 molecules of each generation. Below each molecule are the Fitness, logP, SA, ring penalty and discriminator scores
2. results_0_i:  
   Each sub-directory is named by the generation. The smile strings (ordered by fitness) and corresponding molecular properties are provided as text
   files: 'smiles_ordered.txt', 'logP_ordered.txt', 'sas_ordered.txt', 'ringP_ordered.txt', 'discrP_ordered.txt'. 
   Outside the sub-directories is the information about the best molecules of a generation. 
3. saved_models_0_i:  
   The trained discriminators after each generation. Please Note: We did not make use of the discriminator predictions in the Fitness for this experiment (beta is set to 0).


# Directory Navigator: 
The code for this repository is arranged based on the experiments of the paper. Particularly: 
- [Experiment 4.1: ](https://github.com/akshat998/GA/tree/master/4.1) Unconstrained optimization and comparison with other generative models
- [Experiment 4.2: ](https://github.com/akshat998/GA/tree/master/4.2) Long term experiment with a time-dependent adaptive penalty
- [Experiment 4.3: ](https://github.com/akshat998/GA/tree/master/4.3) Analysis of molecule classes explored by the GA
- [Experiment 4.4: ](https://github.com/akshat998/GA/tree/master/4.4) Constrained optimization
- [Experiment 4.5: ](https://github.com/akshat998/GA/tree/master/4.5) Simultaneous logP and QED optimization
- [Experiment 4.6: ](https://github.com/akshat998/GA/tree/master/4.6) Modification of the hyperparameter beta
- [CLEAN: ](https://github.com/akshat998/GA/tree/master/CLEAN) A cleaner version of the code (recommend for running your experiments)

Instructions on running the code are provided in the above links. Please note that the code has been parallelized based on the number of CPU cores for quick property evaluations.

Due to the large size of the repository, we have created a seperate branch that contains outputs from all the eperiment. For this option, please run (note: this is a 4GB branch, and needs 20mins of cloning time): 
```
git clone --single-branch --branch paper_results https://github.com/akshat998/GA.git
```




# Questions, problems?

Make a github issue 😄. Please be as clear and descriptive as possible. Please feel free to reach
out in person: (akshat[DOT]nigam[AT]mail[DOT]utoronto[DOT]ca)

