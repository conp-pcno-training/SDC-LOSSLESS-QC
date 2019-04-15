---
title: "Making Decisions About the Data"
teaching: 0
exercises: 0
questions:
- "What decisions can be made about the data?"
- "How do I make decisions about components and time periods?"
objectives:
- "Understand the benefits and necessity of a manual quality check procedure."
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

The Lossless pipeline marked up your data based on the parameters in the configuration files. During the quality check procedure you will be visually inspecting the data and making decisions about components and time periods.

During the quality check, our goal is to remove components or time periods that contain artefacts. In EEG analysis, an artefact is any period of activation that does not represent cortical signal. Artefacts can be biological (eye blinks, lateral eye movements, muscle movements, hearbeat, etc.) or environmental (screen refresh rates, channel noise from bad electrodes, and other non-biological electromagnetic signals from the surrounding environment). Most artefacts can be identified based on unusually high frequencies or amplitudes compared to those of typical cortical signal. 

Unfortunately, there is no exact science to determining whether something is or isn't an artefact, and therefore some artefacts will be difficult to identify because they are ambiguous, meaning they may or may not still contain cortical data. These decisions will be more subjective, and based on a number of qualitative factors. Nonetheless, with a bit of practice most artefacts become easy to identify, and the best decision should be fairly obvious.

The pipeline will manually mark out components when ICLabel considers them primarily (i.e. eye, channel noise, muscle, heart, and line noise components). These components will have a gray manual mark flag and will be grayed out at the beginning of the quality check procedure. You will scroll through the data and make decisions about removing components and time periods that are artefactual.

**NOTE:** When making decisions about components, only remaining time periods should be considered because time periods with a manual marking are already marked for removal.

> ## Example 1
> 
> Component has an artefact and the rest of the component is flat.
> ![Example 1]({{ page.root }}/fig/qc_flowchart_01.png){:height="580px" width="408px"}
> 
> {: .source}
>
> > ## Solution
> >
> > Add image of component plot corresponding to this example (FIXME).
> >
> > {: .output}
> {: .solution}
{: .challenge}

> ## Example 2
> 
> The component is not flat, but the artefact is relatively small and might be coming from a true cortical source and a small number of channels are affected.
> ![Example 2]({{ page.root }}/fig/qc_flowchart_02.png){:height="580px" width="408px"} 
>
> {: .source}
>
> > ## Solution
> >
> > Add image of component plot corresponding to this example (FIXME).
> >
> > {: .output}
> {: .solution}
{: .challenge}

> ## Example 3
> 
> The component is not flat, the artefact is large and/or affects many channels and components.
> ![Example 3]({{ page.root }}/fig/qc_flowchart_03.png){:height="580px" width="408px"}
> 
> {: .source}
>
> > ## Solution
> >
> > Add image of component plot corresponding to this example (FIXME).
> >
> > {: .output}
> {: .solution}
{: .challenge}

> ## Example 4
> 
> The component is not flat, the artefact is large and/or affects many channels, but it is isolated to one or two components which also have other artefact in them.
> ![Example 4]({{ page.root }}/fig/qc_flowchart_04.png){:height="580px" width="408px"}
> 
> {: .source}
>
> > ## Solution
> >
> > Add image of component plot corresponding to this example (FIXME).
> >
> > {: .output}
> {: .solution}
{: .challenge}

> ## Example 5
> 
> The component is not flat, the artefact is large and/or affects many channels, but it is isolated to one or two components with no other artefacts in them.
> ![Example 5]({{ page.root }}/fig/qc_flowchart_05.png){:height="580px" width="408px"}
> 
> {: .source}
>
> > ## Solution
> >
> > Add image of component plot corresponding to this example (FIXME).
> >
> > {: .output}
> {: .solution}
{: .challenge}

> ## Example 6
> 
> The component is not flat, the artefact is large and/or affects many channels, it is isolated to one or two components with only a few other artefacts in them, and the topos and ICLabel info for the components suggest a cortical signal.
> ![Example 6]({{ page.root }}/fig/qc_flowchart_06.png){:height="580px" width="408px"}
> 
> {: .source}
>
> > ## Solution
> >
> > Add image of component plot corresponding to this example (FIXME).
> >
> > {: .output}
> {: .solution}
{: .challenge}

> ## Example 7
> 
> The component is not flat, the artefact is large and/or affects many channels, it is isolated to one or two components with only a few other artefacts in them, but the topos and ICLabel info for the components do not suggest a cortical signal.
> ![Example 7]({{ page.root }}/fig/qc_flowchart_07.png){:height="580px" width="408px"}
> 
> {: .source}
>
> > ## Solution
> >
> > Add image of component plot corresponding to this example (FIXME).
> >
> > {: .output}
> {: .solution}
{: .challenge}

> ## Example 8
> 
> The component is not flat, the artefact is large and/or affects many channels, it is isolated to one or two components with only a few other artefacts in them, and the topos and ICLabel info suggest a potentially cortical or mixed signal.
> ![Example 8]({{ page.root }}/fig/qc_flowchart_08.png){:height="580px" width="408px"}
> 
> {: .source}
>
> > ## Solution
> >
> > Add image of component plot corresponding to this example (FIXME).
> >
> > {: .output}
> {: .solution}
{: .challenge}


{% include links.md %}

