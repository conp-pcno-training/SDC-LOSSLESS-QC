---
layout: lesson
root: .  # Is the only page that doesn't follow the pattern /:path/index.html
permalink: index.html  # Is the only page that doesn't follow the pattern /:path/index.html
---

This tutorial will focus on the manual quality control (QC) procedure. We will discuss why it is important, how to set up MATLAB and EEGLAB to perform this procedure, and how to make decisions about the data.  

The QC procedure is the process of reviewing the decisions the pipeline has made about the data. During this step you can manually remove time periods or components that contain artefacts, as well as manually adding back time or components that the pipeline has marked for removal. This procedure is necessary to ensure accurate decisions have been made because automatic classification of components is not always perfect.

> ## Prerequisites
- MATLAB
- All of the previous BIDS EEG, and Lossless pipeline lessons
- Familiarity with EEGLAB, and the Batch Context and Vised Marks plugins
{: .prereq}

{% include links.md %}
