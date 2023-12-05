# Backdoor_Attack_DNN

Project Report: Pruning Defense for Backdoor Detection in BadNets
AG8766
ML for cyber security- Fall 2023

Methodology:
- Objective: To implement the pruning defense for detecting backdoors in BadNets.
- Approach: 
    - Use BadNet B and prune its last pooling layer by removing channels in decreasing order of average activation values over the validation set.
    - Measure new validation accuracy after each channel pruning.
    - Stop pruning when validation accuracy drops at least X% below the original accuracy to create the new pruned BadNet B'.
    - Design GoodNet G to classify test inputs:
        - For each test input, run it through both B and B'.
        - If classification outputs are the same (class i), output class i; otherwise, output N+1.

Steps:
1. Pruning BadNet B:
    - Load BadNet B trained on YouTube Face dataset.
    - Identify the last pooling layer and measure average activation values over the validation set.
    - Remove one channel at a time from the last pooling layer based on decreasing activation values.
    - Evaluate new validation accuracy after each channel pruning.
    - Stop pruning when the accuracy drops by X% from the original accuracy, creating the pruned BadNet B'. X here is {2%, 4%, 10%}

2. Designing GoodNet G:
    - Implement GoodNet G to classify test inputs using both B and B' models.
    - Compare classification outputs from B and B':
        - If they match (class i), output class i.
        - If they differ, output N+1.

Understanding:
- Pruning Defense:
    - Pruning removes channels based on their impact on validation accuracy, reducing the model's susceptibility to backdoors.
    - It creates a pruned BadNet B' that maintains high accuracy on clean data while being less vulnerable to backdoors.

- GoodNet G:
    - G leverages the comparison between B and B' outputs to detect potential backdoors.
    - When discrepancies occur, it signals a potential backdoor, flagging the output as N+1.

 Evaluation and results:

 
	
Graph:
 


 
