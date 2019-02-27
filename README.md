# <font size=6, face="Times">Data and scripts used in the following paper<font>
<br/>
<font size=5, face="Times"><b>Citation:</b></font><br/>
<font size=4, face="Times">Xiao-Fei Yang, Yuan-Ke Zhou, Lin Zhang, Yang Gao, and Pu-Feng Du. Predicting lncRNA subcellular localization using unbalanced pseudo-k nucleotide compositions. 2019 (submitted)</font><br/>
<font size=5, face="Times"><b>Dataset</b></font>
<br/>
<font size=4, face="Times">The information of 644 lncRNA sequences can be found in the folder named Dataset.</font>
<br/>
<font size=5, face="Times"><b>Physicochemical properties</b></font><br/>
<font size=4, face="Times">
In this paper, we use 10 kinds of physicochemical properties for the 16 dinucleotides. The original value can be found in the file physiochemical.csv. Each row represents a kind of physicochemical property. They are shift, slide, rise, tile, roll, twist, stack energy, entropy, free energy and enthalpy, respectively. Each column represents a kind of dinucleotide. They are AA, AC, AG, AU, CA, CC, CG, CU, GA, GC, GG, GU, UA, UC, UG and UU, respectively.
</font><br/>
<font size=5, face="Times"><b>Scripts</b></font>
<br/>
<font size=4, face="Times">In this paper, we implement our method in Python.<br/>
<b>k-mer_nucleotide_composition.ipynb</b><br />
This script can calculate the k-mer nucleotide composition of lncRNA sequences. In this paper, we set the parameter k as 8. As a result, we can obtain 4<sup>8</sup>=65536 dimensional feature vector for each lncRNA sequence. Meanwhile, we store the features information in the file k_mer.zip and the labels information in the file target.npy.<br />
<b>sequence_order_correlated_factors.ipynb</b><br/>
This is the script used to calculate the sequence order correlated factors of lncRNA sequences. The argument lambda_scale represents the parameter <a href="https://www.codecogs.com/eqnedit.php?latex=$\lambda$" target="_blank"><img src="https://latex.codecogs.com/gif.latex?$\lambda$" title="$\lambda$" /></a> in Eq.6 of our paper and can be set to any value less than L-2, where L represents the length of a lncRNA sequence. Here, we set the value of the argument lamada_scale as 14, as we can obtain the maximum accuracy when the parameter <a href="https://www.codecogs.com/eqnedit.php?latex=$\lambda$" target="_blank"><img src="https://latex.codecogs.com/gif.latex?$\lambda$" title="$\lambda$" /></a>=14. We store the information of the sequence order correlated factors in theta_list.npy.<br/>
<b>maximum_overall_accuracy.ipynb</b><br/>
We use this script to obtain the maximum overall accuracy. Firstly, we concatenate the two parts of the feature vector: the 8-mer nucleotide composition and the sequence order correlated factors when <a href="https://www.codecogs.com/eqnedit.php?latex=$\lambda$" target="_blank"><img src="https://latex.codecogs.com/gif.latex?$\lambda$" title="$\lambda$" /></a>=14. Secondly, we use the feature selection thchnique based on ANOVA to obtain the optimal feature subset. Note, for the sake of simplicity, we set the number of features as 11220. The reason can be found in Section 3.1 of our paper. Finally, we can obtain the maximum overall accuracy of 88.82% by using 5-fold cross validation. Meanwhile, the best values for parameters C and gamma of SVM can be obtained, which are 2<sup>8</sup> and 2<sup>-13</sup>, respectively.<br/>
<b>four_metrics.ipynb</b><br/>
This script is used to calculate the four metrics in Section 2.5 of our paper. To begin with, we concatenate the two parts of the feature vector and obtain the optimal feature subset. Then, we use the leave-one-out cross-validation to calculate the confusion matrix. Lastly, we calculate the four metrics successively.<br />
<b>ROC_curve.ipynb</b><br/>
This script describes the drawing process of the ROC curve. After obtaining the optimal feature subset, we obtain the "certainty score" of a lncRNA sequence for each class by using decision_function. Finally, We plot the ROC curve. Note, for this imbalanced multclass learning, we plot the micro-average ROC curve since this method takes label imbalance into account.  
</font>


