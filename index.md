---
layout: lesson
root: .  # Is the only page that doesn't follow the pattern /:path/index.html
permalink: index.html  # Is the only page that doesn't follow the pattern /:path/index.html
---

This tutorial will focus on the manual quality check (QC) procedure. We will discuss why it is important, how to set up MATLAB and EEGLAB to perform this procedure, and how to make the most appropriate decisions in terms of which components and/or time periods to mark for removal.  

The quality check (QC) procedure is the process of reviewing the decisions the pipeline has made about your data. During this step you can manually remove time periods that are messy and components that contain artefacts, as well as manually adding back time or components that the pipeline has marked for removal. Machine classification of components is not perfectly accurate, so it is still necessary to visually inspect the scroll data to ensure all the correct decisions had been made.

- Quality check is a manual procedure performed on data after it has gone through the pipeline.

- The main output files from the pipeline will be in `*_ll.set` format.

- Before the QC procedure can be run, files must first be QC-initialized. This involves running the `qc_init.htb` script on the files (in MATLAB 2014b or later).

- `qc_init.htb`: performs the IC Label classification procedure.

- After the `qc_init.htb` script is run, you will have a corresponding `*_qc.set` file.

- The QC procedure is run on the `*_qc.set` files.

> ## Prerequisites
- MATLAB
- All of the previous BIDS, BIDS EEG, and Lossless pipeline lessons
- Familiarity with EEGLAB, and the Batch Context and Vised Marks plugins
{: .prereq}

{% include links.md %}
