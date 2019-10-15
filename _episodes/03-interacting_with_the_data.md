---
title: "Interacting with the Data"
teaching: 15
exercises: 45
questions:
- "How do I actually interact with the data during quality control?"
objectives:
- "Understand how to use the keyboard and mouse to interact with the EEG scroll plots to flag and unflag components and periods of time."
keypoints:
- "Left-clicking toggles the highlight tool"
- "Right-clicking over a component toggles the manual mark"
- "Pressing the **'m'** key over a highlighted time period will add the manual mark"
- "Pressing **[shift + m]** over a highlighted time period will remove the manual mark"
- "Pressing the **'a'** key will mark a component ambiguous"
- "The overlay can be turned on and off by pressing **'o'** and updated by pressing **'u'**"
---

The EEG component data window is the main window you will be interacting with during the procedure. Below is a table containing all of the actions that are possible during QC.

| Action | Instructions |
| ------- | -----------------|
| **Removing or adding back in a component** | Components that are marked for removal will be "grayed out" and will have a gray flag beside the component on the left hand side of the component data window. To toggle the state of the manual mark on a component, right click it. |
| **Marking out time** | To reject a given period of time, begin by left clicking the beginning the artefactual time period. Move your mouse to the end of the artefactual time period and left click again. This will add a green highlight to the selected time period. Next, hover the mouse over the highlighted time period and click **'m'** on the keyboard to add the gray manual mark. |
|  **Adding time back in** | Time that the pipeline marked for removal can also be added back in. If you hover over the selected area that you want to add back in and press **[shift + m]**, the manual marking for this time period will be discarded. |
| **Marking a component ambiguous** | The ambiguous mark is used to identify components that are difficult to classify as artefact. To mark a component as ambiguous, hover over it, and press **a**. The component shopuld now appear to be blue. To remove this mark, repeat the process. |
| **Using the overlay** | To better visualize changes to the scalp data, the EEG **channel** figure can display an overlay. To enable this feature, click into the EEG **channel** window to make it your current focus, and press **o**. Data in blue, is the EEG data with no artefacts removed. Data in gray, reflect the changes made by rejecting various components. To update this figure after toggling components, make the EEG **channel** window your focus by cliciking into it, and pressing **u**. This ferature is often used to confirm if a particular artefact is contained in a given componenet. The overlay can be turned off by pressing the **'o'** button, with the EEG **channel** window as your focus. |

> ## Note
> The number of channels or components displayed can be changed by navigating to the drop down menu under **Settings->Number of Channels to display**.
>
> {: .source}
{: .callout}

{% include links.md %}

