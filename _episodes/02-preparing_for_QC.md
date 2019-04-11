---
title: "Preparing for the Quality Check Procedure"
teaching: 0
exercises: 0
questions:
- "How do I get my files from the lossless pipeline ready for quality checking?"
objectives:
- "Preparing files from the pipeline for QC."
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

1. Open MATLAB (2014b or later).

2. Navigate to the pipeline root directory (in this tutorial, that will be the face_13 folder).

3. In the MATLAB Command Window, set the path for eeglab and its plugins, and open eeglab: 

    `>> addpath code`  
    `>> lossless_path`  
    `>> eeglab`

4. Add the matconvnet folder and its subdirectories to the MATLAB path: 

    `>> addpath(genpath('derivatives/lossless/code/dependencies/eeglab_asr_amica/plugins/ICLabel0.3/matconvnet'));`

5. Finally, compile the matconvnet binaries for IC Label:

    `>> vl_compilenn` (this only has to be done once per study)

6. To run the `qc_init.htb` script, go to the main EEGLAB window and click **File->Batch->Run History Template Batch**.

7. In the **Run History Template Batch** window, add a Context configuration file. The default file will be sufficient for this task: `derivatives/loseless/code/config/contextconfig.cfg`. 

8. Click **History File** and add the `qc_init.htb` script located in `derivatives/loseless/code/scripts/`.

9. Open up a terminal window, and navigate to your local project directory:

    `>> cd path/to/project/directory/face_13/`

10. List all the data files you’d like to run through the pipeline. This can be done using the find command. If using the BIDS directory structure, simply type:

    `>> find derivatives/lossless/sub-* -type f -name "*_ll.set"`

11. This will print a list of all your `*_ll.set` files, including the path, which you can then copy straight from the terminal into the **file** field in the **Run History Template Batch** window, with one path/filename per line.

12. Click **Ok** to start the qc_init batch process.

{% include links.md %}

