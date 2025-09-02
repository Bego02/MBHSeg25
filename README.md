
# MBHSeg25

## Description

Inference repository for the MICCAI 2025 - MBHSEG Mulitclass Brain Hemorrhage Segmentation Challenge

Challenge Website: https://www.mbhseg.com/

Developed by the Charité Lab for AI in Medicine (CLAIM) research group at Charité University Hospital, Berlin, main developer and person to contact: Begüm Tahhan (begumtahhan@gmail.com) 

#### Please cite the 3 articles in the references section if you use this model in your research

### Model Details

#### 1.Input:
   - MICCAI25 training and validaton set is used

#### 2.Models Used:
   - **ResEncXL** variation of nnUNet models is utilized: Trained using a 5-fold cross-validation approach.
   - Focal-Dice loss function combination is used.

### Postprocessing Steps

- Connected Component Processing:
  
  - All voxels of connected components that contain both Subdural and Epidural hemorrhage are reassigned to the predominant hemorrhage class.

- Small Hemorrhage Removal:

  - If a segmentation contains fewer than 25 voxels of Subarachnoid (SAH), Epidural, or Subdural hemorrhage, they are excluded and reassigned to the background class.


## Inference

To set up the environment and install the necessary dependencies, follow these steps:

### Build conda environment

1.Create and Activate a Virtual Environment

    conda create -n MBHSEG25 python==3.11.10  
    conda activate MBHSEG25
    
2.Install the requirements
    
    cd CLAIM_MBHSeg25
    pip install -r requirements.txt

### Download model weights

Download and place models inside **models** folder:

   ```
   CLAIM_MBHSeg25/
   |– models/
   |– nnunetv2/
   |– requirements.txt
   |– submission.py
   |– README.md
   ```
    

Download model weights from: [(https://drive.google.com/drive/folders/19trjs9Z0zZlK6-2dsA8AAg4CT1Uyts3N?usp=sharing)]


### Running inference

 Make sure that the conda environment is active
    
    conda activate MBHSEG25  


Run the submission.py specifying an input folder and output folder
Generic:

    python submission.py --input_folder absolute_path_to_some_folder_containing_niftis --output_folder absolute_path_to_desired_output_folder

Example on CLAIMs local computer:

    python submission.py --input_folder /media/CLAIM/storage_4tb/Submission_BHDS/folder_to_predict --output_folder /media/CLAIM/storage_4tb folder_to_predict_segmented

### References
- 1. Flanders AE, Prevedello LM, Shih G, Halabi SS, Kalpathy-Cramer J, Ball R, Mongan JT, Stein A, Kitamura FC, Lungren MP, Choudhary G, Cala L, Coelho L, Mogensen M, Morón F, Miller E, Ikuta I, Zohrabian V, McDonnell O, Lincoln C, Shah L, Joyner D, Agarwal A, Lee RK, Nath J, the RSNA-ASNR 2019 Brain Hemorrhage CT Annotators. Construction of a machine learning dataset through collaboration: the RSNA 2019 brain CT hemorrhage challenge. Radiology: Artificial Intelligence. 2020 Apr 29;2(3):e190211.
- 2. Isensee, F., Jaeger, P.F., Kohl, S.A.A. et al. nnU-Net: a self-configuring method for deep  learning-based biomedical image segmentation. Nat Methods 18, 203–211 (2021).  https://doi.org/10.1038/s41592-020-01008-z) 
- 3. Lin, T.-Y., Goyal, P., Girshick, R., He, K., & Dollár, P. (2020). Focal loss for dense object detection. IEEE Transactions on Pattern Analysis and Machine Intelligence, 42(2), 318–327. https://doi.org/10.1109/TPAMI.2018.2858826
