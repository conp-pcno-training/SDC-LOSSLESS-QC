---
title: "Making Decisions About the Data"
teaching: 25
exercises: 0
questions:
- "What decisions can be made about the data?"
- "How do I make decisions about components and time periods?"
objectives:
- "Understand the benefits and necessity of a manual quality check procedure."
keypoints:
- "We need to establish an approach that allows us to reliably identify artefacts based on as few subjective factors as possible."
- "Using the flow chart, most artefacts can be reliably identified and a consistent decision can be made based on the properties of the components."
- "Despite efforts to create a fully objective set of decision criteria, there will still be cases that are ambiguous. In these cases, we need to use our best judgement to decide what to reject and what to leave in."
---

## Description

The Lossless pipeline marked up your data based on the parameters in the configuration files. During the quality check procedure you will be visually inspecting the data and making decisions about components and time periods.

During the quality check, our goal is to remove components or time periods that contain artefacts. In EEG analysis, an artefact is any period of activation that does not represent cortical signal. Artefacts can be biological (eye blinks, lateral eye movements, muscle movements, hearbeat, etc.) or environmental (screen refresh rates, channel noise from bad electrodes, and other non-biological electromagnetic signals from the surrounding environment). Most artefacts can be identified based on unusually high frequencies or amplitudes compared to those of typical cortical signal.

Unfortunately, there is no exact science to determining whether something is or isn't an artefact, and therefore some artefacts will be difficult to identify because they are ambiguous, meaning they may or may not still contain cortical data. These decisions will be more subjective, and based on a number of qualitative factors. Nonetheless, with a bit of practice most artefacts become easy to identify, and the best decision should be fairly obvious.

The pipeline will manually mark out components when ICLabel considers them primarily (i.e. eye, channel noise, muscle, heart, and line noise components). These components will have a gray manual mark flag and will be grayed out at the beginning of the quality check procedure. You will scroll through the data and make decisions about removing components and time periods that are artefactual.

**NOTE:** When making decisions about components, only remaining time periods should be considered because time periods with a manual marking are already marked for removal.

## Decision Flow Chart

![QC Decision Flow Chart]({{ page.root }}/fig/qc_flowchart.png "QC Decision Flow Chart"){:height="580px" width="408px"}
*This decision flow chart can be used during the quality check procedure when you come across a component with an artefact in it. This will help you make a decision about the component using information that is provided to you.*

## Examples

> ## Case 1
> 
> Component has an artefact and the rest of the component is flat.
> 
> {: .source}
>
> > ## See flow chart
> > ![Flow Chart 1]({{ page.root }}/fig/qc_flowchart_01.png){:height="580px" width="408px"}
> >
> > {: .output}
> {: .solution}
>
> > ## Example 1
> >
> > ![Scroll Plot 1a]({{ page.root }}/fig/qc_example_01a.png)
> > Component 11 in this example has a large artefact that is affecting the EEG channel data and the rest of the component is flat. Because the rest of the component does not appear to contain much cortical data, it is preferable to remove the component with the isolated artefact compared to removing time.
> >
> > {: .output}
> {: .solution}
>
> > ## Example 2
> >
> > ![Scroll Plot 1b]({{ page.root }}/fig/qc_example_01b.png)
> > There are many large artefacts in otherwise flat components. Although there are several artefacts at the same time, they are all occurring in components that are otherwise flat. Removing each of these components would be the best decision here.
> >
> > {: .output}
> {: .solution}
{: .challenge}

> ## Case 2
> 
> The component is not flat, but the artefact is relatively small and might be coming from a true cortical source and a small number of channels are affected.
> 
> {: .source}
>
> > ## See flow chart
> > ![Flow Chart 2]({{ page.root }}/fig/qc_flowchart_02.png){:height="580px" width="408px"}
> >
> > {: .output}
> {: .solution}
>
> > ## Example 1
> >
> > ![Scroll Plot 2]({{ page.root }}/fig/qc_example_02.png)
> > At 1141 seconds, there is what appears to be an artefact in component 11. However when looking at the EEG channel data, there is no significant artefact at this time point. Using the projected overlay is particularly helpful for determining that data with the remaining components is clean. Because the EEG channel data appears to be within a reasonable range across all channels at that time point, we can leave the component and time period in.
> >
> > {: .output}
> {: .solution}
{: .challenge}

> ## Case 3
> 
> The component is not flat, the artefact is large and/or affects many channels and components.
> 
> {: .source}
>
> > ## See flow chart
> > ![Flow Chart 3]({{ page.root }}/fig/qc_flowchart_03.png){:height="580px" width="408px"}
> >
> > {: .output}
> {: .solution}
>
> > ## Example 1
> >
> > ![Scroll Plot 3a]({{ page.root }}/fig/qc_example_03a.png)
> > During the time periods around 585-587 seconds and 597-599 seconds, there are several components that contain artefacts. For these time periods, we would answer no to the first question because several components that have artefacts are not flat. For the second question, we would answer yes because several channels are being affected by these artefacts in the scalp EEG data. For the third question, we would answer yes because there are multiple components with artefacts during this time period. In this example, we would prefer to flag the time period for removal over removing every component that has an artefact. We would have to remove too many components in order to clean up this time period so it is better to remove the time period instead. We can also use the orange AMICA marks to help make this decision. The lighter highlight that is seen during this time period indicates that the three parallel AMICA procedures did not replicate during this time period.
> >    
> >
> > {: .output}
> {: .solution}
>
> > ## Example 2
> >
> > ![Scroll Plot 3b]({{ page.root }}/fig/qc_example_03b.png)
> > At the time period around 597-599 seconds, several components have artefacts and the AMICA orange highlight is lighter during this period. Removing this time period would be the best decision here.
> >
> > {: .output}
> {: .solution}
>
> > ## Example 3
> >
> > ![Scroll Plot 3c]({{ page.root }}/fig/qc_example_03c.png)
> > At the time period around 542-544 seconds, several components have artefacts and the AMICA orange highlight is lighter during this period. Removing this time period would be the best decision here.
> >
> > {: .output}
> {: .solution}
{: .challenge}

> ## Case 4
> 
> The component is not flat, the artefact is large and/or affects many channels, but it is isolated to one or two components which also have other artefact in them.
> 
> {: .source}
>
> > ## See flow chart
> > ![Flow Chart 4]({{ page.root }}/fig/qc_flowchart_04.png){:height="580px" width="408px"}
> >
> > {: .output}
> {: .solution}
>
> > ## Example 1
> >
> > ![Scroll Plot 4a]({{ page.root }}/fig/qc_example_04a.png)
> > ![Scroll Plot 4b]({{ page.root }}/fig/qc_example_04b.png)
> > The top cortical components are mixed with slow waves (sweat artefacts). This is an ambiguous case because on the one hand we definitely want to remove the sweat artefacts, but on the other hand we don't want to remove any cortical data. In this case we would lean towards removing these components, but we ultimately need to decide based on the projected overlay whether or not too much good cortical data appears to be removed from the scalp waveforms.
> >     
> > If we use the flow chart on the top two components, we would answer no to the first question because the rest of the components aren't flat. We would answer yes to the second question because the artefacts are substantially affecting the EEG channel data, and we would answer no to the third question because for most of the time periods, it is only 2 components that have large artefacts. The components have artefacts that are continually affecting the EEG channel data, so we would answer yes to question 4, which leads to marking the components as ambiguous and flagging them for removal. The artefacts are occurring too often so removing the time period for each artefact is not an option. The artefacts are also isolated to the top two components meaning that removing these components would remove the artefacts from the channel data. Although the component does appear to have some good cortical data, in this case it is best to remove these components, because the resulting projection does not appear to visibly affect areas of good cortical signal, meaning we are losing little to no cortical signal by removing these components. 
> > 
> > {: .output}
> {: .solution}
{: .challenge}

> ## Case 5
> 
> The component is not flat, the artefact is large and/or affects many channels, but it is isolated to one or two components with no other artefacts in them.
> 
> {: .source}
>
> > ## See flow chart
> > ![Flow Chart 5]({{ page.root }}/fig/qc_flowchart_05.png){:height="580px" width="408px"}
> >
> > {: .output}
> {: .solution}
>
> > ## Example 1
> >
> > Add image of component plot corresponding to this example (FIXME).
> >
> > {: .output}
> {: .solution}
{: .challenge}

> ## Case 6
> 
> The component is not flat, the artefact is large and/or affects many channels, it is isolated to one or two components with only a few other artefacts in them, and the topos and ICLabel info for the components suggest a cortical signal.
> 
> {: .source}
>
> > ## See flow chart
> > ![Flow Chart 6]({{ page.root }}/fig/qc_flowchart_06.png){:height="580px" width="408px"}
> >
> > {: .output}
> {: .solution}
>
> > ## Example 1
> >
> > Add image of component plot corresponding to this example (FIXME).
> >
> > {: .output}
> {: .solution}
{: .challenge}

> ## Case 7
> 
> The component is not flat, the artefact is large and/or affects many channels, it is isolated to one or two components with only a few other artefacts in them, but the topos and ICLabel info for the components do not suggest a cortical signal.
> 
> {: .source}
>
> > ## See flow chart
> > ![Flow Chart 7]({{ page.root }}/fig/qc_flowchart_07.png){:height="580px" width="408px"}
> >
> > {: .output}
> {: .solution}
>
> > ## Example 1
> >
> > Add image of component plot corresponding to this example (FIXME).
> >
> > {: .output}
> {: .solution}
{: .challenge}

> ## Case 8
> 
> The component is not flat, the artefact is large and/or affects many channels, it is isolated to one or two components with only a few other artefacts in them, and the topos and ICLabel info suggest a potentially cortical or mixed signal.
> 
> {: .source}
>
> > ## See flow chart
> > ![Flow Chart 8]({{ page.root }}/fig/qc_flowchart_08.png){:height="580px" width="408px"}
> >
> > {: .output}
> {: .solution}
>
> > ## Example 1
> >
> > Add image of component plot corresponding to this example (FIXME).
> >
> > {: .output}
> {: .solution}
{: .challenge}


{% include links.md %}
