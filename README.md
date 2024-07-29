# OEDISI Transients Algorithm

## Use-Case Development

The transient use case is split into two steps: 

a. Dataset generation 

Dataset generation within the transient use case provide sufficient training/validation dataset for the follow-up transient analysis algorithms. To obtain the dataset from a specific test model with certain level of PV penetration, the user will first pick a model in ATP format from the OEDI repository. The test model originates with different steady state settings, including the loading condition and PV capacity, which forms multiple ATP net files. Then the user has the option to modify the transient state settings or not. If so, the transient state settings will be edited under the user’s local workstation. After all the scenarios are designed and prepared, the ATP simulation will generate the datasets in the corresponding ATP format. Lastly, the user has to implement data processing step and then output the required data formats.

b. Event detection and identification algorithms.

This use-case provides containerized data-driven algorithm that takes dataset on workstation and trains the transient algorithm inside the docker container. Upon the completion of training and testing, trained model, training and testing results and plots will be copied from docker container to local station.   

## data_generation_pipeline updates

There are a few updates on the data generation pipeline branch.

-The AtpLoop_all_feeders_PV.py script is modified to run on IEEE13 with a few additional randomization effects to improve the variability of the training data.  
-gen_npz.py is updated to handle the random start time/length variation and to scale voltage and current to p.u. values. It also has a function added to handle files generated in ATPDraw.  
-collect_atpdraw_sims.py is added to simplify the merging of multiple simulations generated with ATPDraw.  
-comtrade_to_csv.py is added to create csv files  

