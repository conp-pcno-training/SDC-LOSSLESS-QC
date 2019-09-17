---
title: "Introduction to the Quality Control Procedure"
teaching: 15
exercises: 45
questions:
- "What decisions can be made about the data?"
- "How do I understand the figures that are presented during quality control?"
- "How do I identify an artefact in the data?"
objectives:
- "Understand how to use the information provided in the figures to make decisions about the data."
- "Understand how to identify artefacts in the data."
keypoints:
- "The goal of the QC procedure is to remove artefacts from the data through marking components and time periods for removal."
---

## Description

The Lossless pipeline marked up your data based on the parameters in the batch configuration files. During the quality control procedure you will be visually inspecting the data and making decisions about components and time periods. 

Our goal is to remove components or time periods that contain artefacts. In EEG analysis, an artefact is any period of activation that does not represent cortical signal. Artefacts can be biological (eye blinks, lateral eye movements, muscle movements, hearbeat, etc.) or environmental (screen refresh rates, channel noise from bad electrodes, etc.). Most artefacts can be identified based on unusually low/high frequencies or amplitudes compared to those of typical cortical signal.

You will scroll through the data and make decisions about removing or leaving in components and periods of time. The manual mark can be added or removed to components and time periods as you QC. When the data is purged following the QC procedure, components, channels, and time periods with a manual mark will be removed.

> ## Note
> When making decisions about components, only remaining time periods should be considered because time periods with a manual marking are already marked for removal.
>
> {: .source}
{: .callout}

## Pipeline Labels

The pipeline will add channel, component, and time marks to your data. These marks are based on various signal quality measurements.

## Channel Pipeline Labels 

When you open a file to perform the QC procedure, there will be channels that have a manual mark and are grayed out. Decisions about marking channels for removal are made based off of parameters provided in the batch configuration files. These decisions can be altered by editing the parameters in the batch configuration files before running the pipeline. 

| Label | Description |
| ------ | --------------- |
| manual | The interactive label (modified by analysts interactively or by a pipeline decision along with other labels) typically used to indicate which channels are considered artefactual for any reason. |
| ch_sd | Pipeline decision flag indicating that channels were too often outliers compared to other channels for the measure of standard deviation of voltage within one second epochs. |
| low_r | Pipeline decision flag indicating that channels were too often outliers compared to other channels for the measure of correlation coefficient to spatially neighbouring channels within one second epochs. |
| bridge | Pipeline decision flag indicating that channels were outliers in terms of having high and invariant correlation coefficients to spatially neighbouring channels. |
| rank | Pipeline decision identifying the channel that has the least amount of unique information (highest average correlation coefficient to spatially neighbouring channels) to be ignored by the independent component analysis to account for the rank deficiency of the average referenced data. |

## Component Pipeline Labels

The `qc_init.htb` script will manually mark out components when ICLabel considers them to be primarily an artefact (i.e. eye, channel noise, muscle, and heart components). These components will have a gray manual mark flag and will be grayed out at the beginning of the quality control procedure. Components are sorted by the percent data variance accounted for, with the top components accounting for a greater percentage of the channel data. Components are shown in different colours based on thier ICLabel classification. The coloured flag on the left side of each component corresponds with the ICLabel classification. A legend for each ICLabel classification can be found at the top left side of the window above the component scroll data. Some components also have a blue flag on the left side of the data. This blue flag is the ic_rt mark and is given when the component was not replicated across the three runs of the AMICA models. 

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

The EEG component and channel data has marks throughout the file that relate to time. The time marks are independent of the y-axis (these marks are only related to time and are not related to the location of the components). The criteria used to make decisions about time can be edited through changing parameters in the configuration files. When the pipeline has marked time as artefactual, there will be a coloured mark that relates to why that time period is considered messy, as well as a gray manual mark. 

Throughout the whole file there will be an orange AMICA bar. This bar is related to the level of replication between the three parellel AMICA runs. A lighter orange bar indicates that the three AMICA procedures did not replicate during this time period. The orange AMICA bar will not be at some time periods that are marked as artefactual because these time periods did not run through AMICA.

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

![QC Artefact Example]({{ page.root }}/fig/qc_marks_example.png "QC Artefact Example")

This figure is an example of the component EEG data scroll plot. This is the window that you will be interacting with as you QC. As you scroll through the data, ensure that you agree with the decisions that the pipeline made about your data. You will also be looking for artefacts as you scroll through. The above figure has several examples of time periods that the pipeline marked as artefactual for various reasons as well as artefacts that are in components during remaining time periods. 

During the time period of 542-543 seconds, several components have an artefact. These artefact have unusually high amplitudes compared to cortical data and are seen as large spikes. 


{% include links.md %}

