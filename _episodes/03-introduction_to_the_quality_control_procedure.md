---
title: "Introduction to the Quality Control Procedure"
teaching: 15
exercises: 45
questions:
- "What decisions can be made about the data?"
- "How do I understand the figures that are presented during quality control?"
objectives:
- "Understand how to use the information provided in the figures to make decisions about the data."
keypoints:
- "The goal of the QC procedure is to remove artefacts from the data through marking components and time periods for removal."
---

## Description

The Lossless pipeline marked up your data based on the parameters in the configuration files. During the quality control procedure you will be visually inspecting the data and making decisions about components and time periods. 

Our goal is to remove components or time periods that contain artefacts. In EEG analysis, an artefact is any period of activation that does not represent cortical signal. Artefacts can be biological (eye blinks, lateral eye movements, muscle movements, hearbeat, etc.) or environmental (screen refresh rates, channel noise from bad electrodes, etc.). Most artefacts can be identified based on unusually low/high frequencies or amplitudes compared to those of typical cortical signal.

The `qc_init.htb` script will manually mark out components when ICLabel considers them to be primarily an artefact (i.e. eye, channel noise, muscle, and heart components). These components will have a gray manual mark flag and will be grayed out at the beginning of the quality control procedure. Components are sorted by the percent data variance accounted for, with the top components accounting for a greater percentage of the channel data. Components are shown in different colours based on thier ICLabel classification. The coloured flag on the left side of each component corresponds with the ICLabel classification. A legend for each ICLabel classification can be found at the top left side of the window above the component scroll data. Some components also have a blue flag on the left side of the data. This blue flag is the ic_rt mark and is given when the component was not replicated across the three runs of the AMICA models.

The EEG component and channel data has marks throughout the file that relate to time. The location of the marks are independent of the y-axis (these marks are only related to time and are not related to the location of the components). The criteria used to make decisions about time can be edited through changing parameters in the configuration files. When the pipeline has marked time as messy, there will be a coloured mark that relates to why that time period is considered messy, as well as a gray manual mark. 

Throughout the whole file there will be an orange AMICA bar. This bar is related to the level of replication between the three parellel AMICA runs. A lighter orange bar indicates that the three AMICA procedures did not replicate during this time period. The orange AMICA bar will not be at some time periods that are marked as messy because these time periods did not run through AMICA. The blue init_ind mark is an indicator of how far into the file you are and gets darker the farther that you are. 

You will scroll through the data and make decisions about removing or leaving in components and periods of time that may or may not contain artefacts. When the data is purged following the QC procedure, components, channels, and time periods with a manual mark will be removed. The manual mark can be added or removed to components and time periods as you QC and this is how you mark data for removal during purging. 

> ## Note
> When making decisions about components, only remaining time periods should be considered because time periods with a manual marking are already marked for removal.
>
> {: .source}
{: .callout}

## Pipeline Labels

The pipeline will add channel, component, and time marks to your data. These marks are based on various signal quality measurements.

## Channel Pipeline Labels 

| Label | Description |
| ------ | --------------- |
| manual | The interactive label (modified by analysts interactively or by a pipeline decision along with other labels) typically used to indicate which channels are considered artefactual for any reason. |
| ch_sd | Pipeline decision flag indicating that channels were too often outliers compared to other channels for the measure of standard deviation of voltage within one second epochs. |
| low_r | Pipeline decision flag indicating that channels were too often outliers compared to other channels for the measure of correlation coefficient to spatially neighbouring channels within one second epochs. |
| bridge | Pipeline decision flag indicating that channels were outliers in terms of having high and invariant correlation coefficients to spatially neighbouring channels. |
| rank | Pipeline decision identifying the channel that has the least amount of unique information (highest average correlation coefficient to spatially neighbouring channels) to be ignored by the independent component analysis to account for the rank deficiency of the average referenced data. |

## Component Pipeline Labels

| Label | Description |
| ------ | -----------------|
| manual | The interactive label (modified by analysts interactively or by a pipeline decision along with other labels) typically used to indicate which components are considered artefactual for any reason. |
| ic_rt | Pipeline decision flag indicating that components were not replicated across the three parallel AMICA runs. |
| brain | ICLabel 0.3 Mark indicating that the component has cortical characteristics. |
| muscle | ICLabel 0.3 Mark indicating that the component has EMG characteristics. |
| eye | ICLabel 0.3 Mark indicating that the component has EOG characteristics. |
| heart | ICLabel 0.3 Mark indicating that the component has ECG characteristics. |
| line_noise | ICLabel 0.3 Mark indicating that the component has electrical mains noise characteristics. |
| chan_noise | ICLabel 0.3 Mark indicating that the component has channel independence characteristics. |
| other | ICLabel 0.3 Mark indicating that the component could not be confidently classified within any other ICLabel classification. |
| ambiguous | QC procedure rater markup indicating that the component is difficult to classify as either artefact or not. |

## Time Pipeline Labels

| Label | Description |
| -------- | ----------------|
| manual | The interactive label (modified by analysts interactively or by a pipeline decision along with other labels) typically used to indicate which time points are considered artefactual for any reason. |
| init_ind | Continuous variable indicating the initial time point index within the session. |
| mark_gap | Pipeline decision flag indicating that time points are within a short gap between other annotations. | 
| ch_sd | Pipeline decision flag indicating that time points were too often outliers across channels compared to other time points for the measure of standard deviation of voltage within one second epochs. |
| low_r | Pipeline decision flag indicating that time points were too often outliers across channels compared to other time points for the measure of correlation coefficient to spatially neighbouring channels within one second epcohs. |
| logl_init | Log likelihood of initial AMICA decomposition. |
| ic_sd1 | Pipeline decision flag indicating that time points were too often outliers across initial components compared to other time points for the measure of component standard deviation of voltage within one second epochs. |
| logl_A | Log likelihood of final AMICA decomposition (replication A). |
| logl_B | Log likelihood of final AMICA decomposition (replication B). |
| logl_C | Log likelihood of final AMICA decomposition (replication C). |
| ic_sd2 | Pipeline decision flag indicating that time points were too often outliers across final components compared to other time points for the measure of component standard deviation of voltage within one second epochs. |
| ic_dt | Pipeline decision flag indicating that time points were too often outliers across initial components compared to other time points for the measure of component spectral Theta within one second epochs. |
| ic_a | Pipeline decision flag indicating that time points were too often outliers across initial components compared to other time points for the measure of component spectral Alpha within one second epochs. |
| ic_b | Pipeline decision flag indicating that time points were too often outliers across initial components compared to other time points for the measure of component spectral Beta within one second epochs. |
| ic_lg | Pipeline decision flag indicating that time points were too often outliers across initial components compared to other time points for the measure of component spectral Low Gamma within one second epochs. |
| ic_hg | Pipeline decision flag indicating that time points were too often outliers across initial components compared to other time points for the measure of component spectral High Gamma within one second epochs. |

## Examples of Artefacts

![QC Artefact Example]({{ page.root }}/fig/qc_marks_examples.png "QC Artefact Example")

This figure is an example of the component EEG data scroll plot. This is the window that you will be interacting with as you QC. 


{% include links.md %}

