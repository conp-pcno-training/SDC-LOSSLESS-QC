---
title: "Interacting with the Data"
teaching: 15
exercises: 45
questions:
- "How do I make changes while doing the quality check?"
objectives:
- "Understand ..."
keypoints:
- "Right clicking over a component will add or remove the manual marking"
- "Clicking 'm' over a highlighted time period will add the manual mark"
- "Clicking 'a' will mark a component ambiguous"
- "The overlay can be turned on and off by clicking 'o' and updated by clicking 'u'"

---
Throughout the quality check procedure you will be interacting with the various windows. The EEG component data window is the main window you will be interacting with and this is where the marks structure will be saved. 

1. Removing or adding back in a component: Components that are marked for removal will be grayed out and will have a gray flag beside the component on the left hand side of the component data window. To mark out a component you would like removed or to add back a component that has been removed, hover over the component and right click on the mouse. 

2. Marking out time: To mark out time you interact with the component data window. You can using the winrej highlighting tool and left click at the start of the time period that you want to mark for removal and then move the mouse to the end of the time period and left click again. This will highlight the time period blue. Then hover the mouse over the time period and click 'm' on the keyboard to add the gray manual mark. If you want to remove time that has a marking (such as ic_hg), you can hover over the marking and select 's' on the keyboard. This will select that time period and you can then press 'm' to add the manual marking to this time period. 

3. Adding time back in: Time that the pipeline marked for removal can be added back in. If you hover over the selected area that you want to add back in and press 'shift' and 'm' the manual marking will be removed. You can then click on the selected area to remove the blue winrej highlight. 

4. Marking a component ambiguous: The ambiguous mark is used to identify components that are difficult to classify as either artefact or not. To add the manual mark, hover over the component and press 'a' on the keyboard. Marking a component ambiguous will change the component colour to blue, which is helpful to keep track of a component throughout a file. For example, the ambiguous mark can be useful when you are deciding between removing a time period or a component due to isolated artefacts and you want to see if the component has more artefacts throughout the file. 

5. Using the overlay: An overlay of the projected data can be placed on top of the channel EEG data. The overlay shows the data that would be projected back to the scalp from only the remaining components. This means that if a manual mark has been added to a component, the data from that component would not be in the projected data. The projected data can be shown as a gray line on top of the channel EEG data by selecting the EEG channel data window and pressing 'o' on the keyboard. If you mark a component for removal, you can press 'u' to update the projection, because the projection data will change based on what components are marked for removal. The overlay can be turned off by pressing the 'o' button again. 

6. The number of channels or components displayed can be changed by go to Settings > Number of Channels (or Components) to display. 


{% include links.md %}

