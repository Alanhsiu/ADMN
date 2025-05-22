# ADMN Initial Code Repository for Neurips Submission #9553


## Downloading the Datasets
The datasets used in this work are the [GDTM Dataset](https://github.com/nesl/GDTM), [MMFI Dataset](https://ntu-aiot-lab.github.io/mm-fi) and [AVE Dataset](https://sites.google.com/view/audiovisualresearch), which can be downloaded at their respective links


## Running the code

In each dataset/corruptions respective folder, there are a series of scripts titled `neurips...` for training and testing the models:

`neurips_train_stage_1_model.sh`: This trains the stage 1 model on the dataset with a specified LayerDrop rate, creating a model that is robust to different configurations of dropped layers during inference time

`neurips_test_stage_1.sh`: With the trained Stage 1 Model, we can evaluate its performance with various layers dropped out to represent the Naive Alloc., and Image/Audio/Depth only baselines

`neurips_train_scratch.sh`: This script concerns itself with all the models trained from scratch, which are the MNS and Naive Scratch Models.

`neurips_test_scratch.sh`: This script tests all the Unimodal Scratch and Naive Scratch models

`neurips_train_supervised_controller.sh`: This script trains the Corruption Supervised Controller (referred to as ADMN in the work), which leverages the trained Stage 1 model and adds a controller to perform QoI aware layer selection. We train controller with different layer budgets of 6, 8, 12, and 16

`neurips_test_supervised_controller.sh`: This script tests all the different controllers that we trained in the prior script.

`neurips_train_ae_controller.sh`: This script first trains an autoencoder, and then uses the autoencoder weights to initialize the controller. There is not corruption supervision, and the model is purely supervised by the task loss. 

`neurips_test_ae_controller.sh`: We test the models trained in the previous script

`neurips_train_mns.sh`: We train the modality selection networks. They utilize the trained unimodal/multimodal networks and add an additional selector model to choose the appropriate unimodal/multimodal model depending on the input

`neurips_test_mns.sh`: We test the trained MNS models

