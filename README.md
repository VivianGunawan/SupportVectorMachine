# SupportVectorMachine

🗓 Spring 2019 (Had to miss Avengers Endgame premiere coding this)

## Project Description

Classfying numbers from the MNIST dataset using Support Vector Machine sans machine learning libraries.

To address the issue of multiple classes, several methods were implemented

1. One versus Rest

    Train SVM for every class by setting the data points in the specific class with positive label and every other data points not belonging in the class as a negative label. So each data point will have 10 scalar values corresponding to the 10 trained SVM, take the maximum value and set the label of the data point to this class.

2. One versus One

    Train SVM for every possible combination of pairs of classes. Each data point has 45 SVM scalar values corresponding to it. I created a dictionary to keep track of the number of times a certain label wins in the SVM, the label of the data point is determined by the label that wins in most SVM.

3. Directed Acyclic Graph SVM

    Train SVM for every possible combination of pairs of classes. Each data point has 45 SVM scalar values corresponding to it. Start with checking SVM 0 VS 9, and have a list of options for what the label is, do a depth-first search tree traversal, eliminating the label from the list of options as the label lose, the next node that is traversed is the winning label vs another label (if left label wins then left vs right-1, if right label wins then left+1 vs right). As traversal goes, options of label is eliminated until there is only 1 label left which is set as the label of the data point.

### Results

While using the same kernel and c parameter, the voting method ranked from best
to worse in terms of accuracy is 

- One VS The Rest,
- DAGSVM
- One Versus One.

One VS the Rest takes the longest time to train the SVMs because we are training on 4000 data points despite only having to train 10 SVMs.
Both DAGSVM and One VS One took roughly the same time to train the 45 SVMs. However, predicting with the One VS One took slightly longer than DAGSVM.
