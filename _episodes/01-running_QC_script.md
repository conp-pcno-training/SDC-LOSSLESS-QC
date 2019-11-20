---
title: "Running the Quality Control Script"
teaching: 5
exercises: 10
questions:
- "How do I run the quality control procedure?"
- "What does the quality control procedure look like?"
objectives:
- "Understand how to start the quality control procedure."
- "Become familiar with the figures displayed during quality control."
keypoints:
- "The input for running the QC script is `*.edf` files."
- "The QC procedure is a manual review of the decsions the pipeline made. The annontations in the **component** EEG data scroll can be edited to update decisions about the data."
- "The output is `*desc-qc*` files which contain the annotation information."
---

1. Open MATLAB (pre-2014b works fastest) and change your **Current Folder** by navigating to the Lossless pipeline root directory (in this case, `Face13`).

2. Open EEGLAB by typing the following into the command window:

    ```matlab
    >> addpath derivatives/BIDS-Lossless-EEG/code/install
    >> lossless_path
    >> eeglab
    ```

3. If you are using an older version of MATLAB (pre-2014b), you will need to set the default figure renderer to OpenGL by typing the following into the command window:

   
    ```matlab
    >> set(0,'DefaultFigureRenderer','OpenGL');
    ```

4. In the main EEGLAB window, navigate to **File->Vised Configuration**. 

    ![Vised Config Dropdown Menu]({{ page.root }}/fig/visedconfig_dropdown.png)

5. Add the vised configuration file by clicking `| Load vised config |` and then navigate to the config folder (`derivatives/BIDS-Lossless-EEG/code/config/`). Select the file named `vised_config_qc.cfg`, and click `| OK |`. The vised configuration file will load certain settings that are preferable for the QC procedure.

    ![Vised Config Menu]({{ page.root }}/fig/visedconfig.png)

6. In the main EEGLAB window, navigate to **File->Batch->Run History Template Batch**.


7. In the **Run History Template Batch** window, add a Context configuration file by clicking `| Load context config |`. The default file will be sufficient for this task: `derivatives/BIDS-Lossless-EEG/code/config/contextconfig.cfg`. 

8. Click `| History File |` and add the `qc.htb` script located in `derivatives/BIDS-Lossless-EEG/code/scripts/`.

9. Open up a terminal window, and navigate to your local project directory:

    `>> cd path/to/project/directory/Face13`

10. In the terminal, list all the data files you’d like to run through the QC procedure. This can be done using the find command. If using the BIDS directory structure, simply type:

    `>> find . -name "*.edf"`

11. This will print a list of all the files that have run through the pipeline, which you can then copy straight from the terminal into the **file** field in the **Run History Template Batch** window, with one path/filename per line.

12. In the **path** field in the **Run History Template Batch** window, type `derivatives/BIDS-Lossless-EEG`. The history template batch window should look like this:

    ![RunHTB]({{ page.root }}/fig/runhtb.png)

13. Click `| Ok |` to start the QC batch process.

14. Once you click `| Ok |`, the QC windows will open for your first file. The files will open in alphabetical order. Several windows will open for each file you QC, including: 

    <span style="color:red">A.</span> A window that displays the **component** EEG data. This is the window that you will be interacting with as you QC. You will be making your decisions in this window by adding or removing a manual mark for components or time points. Components are sorted by the percent data variance accounted for, with the top components accounting for a greater percentage of the channel data. To scroll through the data, use the `<<` and `>>` buttons in this window. These buttons will scroll both the component EEG data and the channel EEG data windows (Figure C). Your decisions can be saved by clicking the `| Update EEG Structure |` button in **component** EEG data window.

    <span style="color:green">B.</span> A figure that displays the ICLabel classification breakdown for each component.

    <span style="color:blue">C.</span> A window that shows the **channel** EEG data. It also contains an overlay feature that can be toggled on/off or updated while quality controlling. Use of this feature will be explained in subsequent lessons.

    <span style="color:yellow">D.</span> A figure that displays an array of squares corresponding to each 1-second epoch for each component. Each square is colored based on its activation difference from the mean.

    <span style="color:violet">E.</span> Window(s) with a topography for each component. The number label for each topography can be clicked to gain more information.

    <span style="color:orange">F.</span> Upon clicking a number label for a component a figure appears which displays the component's spectrum, dipole location, and a mini scroll plot of the full waveform of the selected component. More information on how to interpret this figure can be found in the [ICLabel Tutorial](https://labeling.ucsd.edu/tutorial/format).

    ![QC Screen Center]({{ page.root }}/fig/qc_screen_center.png)
    ![QC Screen Left]({{ page.root }}/fig/qc_screen_left.png)
    ![QC Screen Right]({{ page.root }}/fig/qc_screen_right.png)
    ![QC Topo Popup]({{ page.root }}/fig/qc_topo_popup.png)

> ## Note
> If you would like to cancel the QC procedure at anytime **without** saving the progress, you will need to force quit the QC script by typing **[Ctrl + C]** in the MATLAB command window.
>
> {: .source}
{: .callout}

{% include links.md %}

