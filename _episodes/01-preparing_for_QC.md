---
title: "Preparing for the Quality Control Procedure"
teaching: 10
exercises: 5
questions:
- "How do I get my files from the lossless pipeline ready for quality controlling?"
objectives:
- "Preparing files from the pipeline for QC."
keypoints:
- "The input is `*_ll.set` files."
- "Currently only works in MATLAB 2014b or later versions."
- "You need to add the **matconvnet** folder (and subfolders) to your path every time."
- "You only need to run the `vl_compilenn` command once per study."
- "The output is `*_qc.set` files ready for the QC procedure."
---

1. Open MATLAB (2014b or later).

2. Navigate to the pipeline root directory (in this tutorial, that will be the Face13 folder).

3. In the MATLAB Command Window, set the path for eeglab and its plugins, and open eeglab: 

    ```matlab
    >> addpath derivatives/BIDS-Lossless-EEG/code/install
    >> lossless_path
    >> eeglab
    ```

4. Add the matconvnet folder and its subdirectories to the MATLAB path: 

    ```matlab
    >> addpath(genpath('derivatives/BIDS-Lossless-EEG/code/dependencies/eeglab_asr_amica/plugins/ICLabel0.3/matconvnet'));
    ```

5. Finally, compile the matconvnet binaries for IC Label:

    ```matlab
    >> vl_compilenn %% this only needs to be done once per study
    ```

6. To run the `qc_init.htb` script, go to the main EEGLAB window and click **File->Batch->Run History Template Batch**.

    ![Run History Template Batch Menu]({{ page.root }}/fig/runhtb_qc_init.png)

7. In the **Run History Template Batch** window, add a Context configuration file by clicking `| Load context config |`. The default file will be sufficient for this task: `derivatives/loseless/code/config/contextconfig.cfg`. 

8. Click `| History File |` and add the `qc_init.htb` script located in `derivatives/loseless/code/scripts/`.

9. Open up a terminal window, and navigate to your local project directory:

    ```bash
    >> cd path/to/project/directory/Face13/
    ```

10. List all the data files you’d like to run through the pipeline. This can be done using the find command. If using the BIDS directory structure, simply type:

    ```bash
    >> find derivatives/BIDS-Lossless-EEG/sub-* -type f -name "*_ll.set"
    ```

11. This will print a list of all your `*_ll.set` files, including the path, which you can then copy straight from the terminal into the **file** field in the **Run History Template Batch** window, with one path/filename per line. If you are using the BIDS folder structure, a simpler method is to use the `| Bids import |` button, navigate to `derivatives/BIDS-Lossless-EEG/`, and click `| Ok |` to automatically populate the list with all the `*_ll.set` files.

12. Click `| Ok |` to start the qc_init batch process.

{% include links.md %}

