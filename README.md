# MBHSeg25

Model Details

    Input:
         MICCAI25 training and validaton set is used

    Models Used:
        ResEncXL variation of nnUNet models is utilized:
        trained using a 5-fold cross-validation approach.

Postprocessing Steps

    Connected Component Processing:
        All voxels of connected components that contain both Subdural and Epidural hemorrhage are reassigned to the predominant hemorrhage class.

    Small Hemorrhage Removal:
        If a segmentation contains fewer than 25 voxels of Subarachnoid (SAH), Epidural, or Subdural hemorrhage, they are excluded and reassigned to the background class.
