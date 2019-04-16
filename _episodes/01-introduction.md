---
title: "Introduction to the Quality Check Procedure"
teaching: 5
exercises: 0
questions:
- "Why is a manual quality check procedure done?"
objectives:
- "Understand the benefits and necessity of a manual quality check procedure."
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

The quality check (QC) procedure is where you will review the decisions the pipeline has made about your data. During this step you can manually remove time periods that are messy and components that contain artefacts, as well as manually adding back time or components that the pipeline has marked for removal. Machine classification of components is not perfectly accurate, so it is still necessary to visually inspect the scroll data to ensure all the correct decisions had been made.

- Quality check is a manual procedure performed on data after it has gone through the pipeline.

- The main output files from the pipenline will be in `*_ll.set` format.

- Before the QC procedure can be done, files must first be QC-initialized. This involves running the `qc_init.htb` script on the files (in MATLAB 2014b or later).

- `qc_init.htb`: performs the IC Label procedure.

- After the `qc_init.htb` script is run, you will have a corresponding `*_qc.set` file. 

- The QC procedure is run on the `*_qc.set` files.

{% include links.md %}

