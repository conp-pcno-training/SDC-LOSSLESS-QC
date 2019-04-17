---
title: "Running the Quality Check Script"
teaching: 5
exercises: 10
questions:
- "How do I run the quality check procedure?"
objectives:
- "Understand how to start the quality check procedure."
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

1. Open MATLAB (pre-2014b works fastest) and change your **Current Folder** by navigating to the Lossless pipeline root directory (in this case, face_13).

2. Open EEGLAB by typing the following into the console window:

    `>> addpath code`  
    `>> lossless_path`  
    `>> eeglab`  

3. Next, set the default figure renderer to be OpenGL. This is usually only necessary in older versions of MATLAB (pre-2014b):

    `>> set(0,'DefaultFigureRenderer','OpenGL');`

4. In the main EEGLAB window, navigate to **File->Vised Configuration**. 

    ![Vised Config Dropdown Menu]({{ page.root }}/fig/visedconfig_dropdown.png)

5. Add the vised configuration file by clicking **Load vised config** and then navigate to the config folder (`derivatives/lossless/code/config/`). Select the file named `vised_config_qc.cfg`, and click **OK**. The vised configuration file will load certain settings that are preferable for the QC procedure.

    ![Vised Config Menu]({{ page.root }}/fig/visedconfig.png)

6. In the main eeglab window, navigate to **File->Batch->Run History Template Batch**.

    ![Run History Template Batch Menu]({{ page.root }}/fig/runhtb_qc.png)

7. In the **Run History Template Batch** window, add a Context configuration file by clicking **Load context config**. The default file will be sufficient for this task: `derivatives/loseless/code/config/contextconfig.cfg`. 

8. Click **History File** and add the `qc.htb` script located in `derivatives/loseless/code/scripts/`.

9. Open up a terminal window, and navigate to your local project directory:

    `>> cd path/to/project/directory/face_13/`

10. List all the data files you’d like to run through the pipeline. This can be done using the find command. If using the BIDS directory structure, simply type:

    `>> find derivatives/lossless/sub-* -type f -name "*_qc.set"`

11. This will print a list of all your QC-initialized `*_qc.set` files, including the path, which you can then copy straight from the terminal into the **file** field in the **Run History Template Batch** window, with one path/filename per line.

12. Click **Ok** to start the QC batch process.

13. Once you click **Ok**, the QC windows will open for your first file. The files will open in alphabetical order. Several windows will open for each file you QC, including: 

    <span style="color:red">A.</span> A window that displays the component EEG data. This is the window that you will be interacting with as you QC.

    <span style="color:green">B.</span> A figure that displays the IC Label classification breakdown for each component.

    <span style="color:blue">C.</span> A window that shows the channel EEG data. It also contains an overlay feature that can be toggled on/off or updated while quality checking. This overlay shows a projection of the remaining components not flagged as "manual" back to the scalp data and overlayed on top of the original EEG data. This allows us to see the effect of removing or adding a component back into the data while we are performing the quality check.

    <span style="color:yellow">D.</span> A figure that displays an array of squares corresponding to each 1-second epoch of each component. Each square is colored based on its activation difference from the mean.

    <span style="color:violet">E.</span> Window(s) with a topography for each component. The number label for each topography can be clicked to gain more information.

    <span style="color:orange">F.</span> Upon clicking a number label for a component a figure appears which displays the component's spectrum, dipole location, and a mini scroll plot of the full waveform of the selected component.

   ![QC Screen Center]({{ page.root }}/fig/qc_screen_center.png)
   ![QC Screen Left]({{ page.root }}/fig/qc_screen_left.png)
   ![QC Screen Right]({{ page.root }}/fig/qc_screen_right.png)
   ![QC Topo Popup]({{ page.root }}/fig/qc_topo_popup.png)

- When you finish the QC procedure, click **Update EEG Structure** and it will save as a `*_qcr.set` and a `*_qcr.fdt` file.

{% include links.md %}

