---
uid: Cube_Feature_Release_10.4.1
---

# DataMiner Cube Feature Release 10.4.1 – Preview

> [!IMPORTANT]
> We are still working on this release. Some release notes may still be modified or moved to a later release. Check back soon for updates!

> [!TIP]
> For release notes for this release that are not related to DataMiner Cube, see [General Feature Release 10.4.1](xref:General_Feature_Release_10.4.1).

## Highlights

*No highlights have been selected yet.*

## New features

#### Spectrum analysis: Zooming inside a spectrum window [ID_37668]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU10] - FR 10.4.1 -->

It is now possible to zoom inside a spectrum window:

- To zoom horizontally, scroll up and down. This has the same effect as altering the frequency span.
- To zoom vertically, scroll up and down while pressing the CTRL key. This has the same effect as altering the amplitude scale.

When you stop scrolling, the new zoom dimensions will be set on the spectrum analyzer device and the screen will be updated with the new data.

> [!IMPORTANT]
>
> - It is only possible to zoom horizontally if the spectrum protocol includes the *Start frequency*, *Stop frequency* and *Frequency span* parameters.
> - It is only possible to zoom vertically if the spectrum protocol includes the *Amplitude scale* parameter.

#### Desktop application: New command-line argument 'UseInitialArgumentsAfterDisconnect' [ID_37888]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU10] - FR 10.4.1 -->

You can now start the DataMiner Cube desktop application with the new command-line argument *UseInitialArgumentsAfterDisconnect=true*.

This argument will make sure that all other arguments you specified when you started the application will again be applied when Cube has to reconnect for some reason.

## Changes

### Enhancements

#### Visual Overview: Enhanced service chain behavior [ID_37645]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU10] - FR 10.4.1 -->

A number of UI enhancements have been made with regard to service chain behavior in visual overviews.

Up to now, in some cases, service chains could get redrawn too often, or shapes would not get redrawn when a service chain was updated. Also, context menus of shapes would not always close when those shapes were updated and context menus would incorrectly show the *Display connectivity* command twice.

#### Spectrum Analysis: Buttons in 'Reference lines' panel, 'Thresholds' panel and 'Measurement Points' panel have been restyled [ID_37752]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU10] - FR 10.4.1 -->

In the *View* tab of a spectrum card, the buttons in the *Reference lines* panel and the *Thresholds* panel as well as the delete buttons in the *Measurement Points* panel have been restyled to match the buttons in the *Markers* panel.

#### Spectrum Analysis: Editing the X-axis and Y-axis labels [ID_37821]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU10] - FR 10.4.1 -->

In a spectrum view, it is now possible to modify the center frequency and reference level.

To modify the center frequency:

1. Click the pencil icon next to the center frequency X-axis label.
1. Use the up/down buttons to change the center frequency.
1. Click *Confirm* or press ENTER.

To modify the reference level:

1. Click the pencil icon next to the reference level Y-axis label.
1. Use the up/down buttons to change the reference level.
1. Click *Confirm* or press ENTER.

> [!NOTE]
> To change the unit of either the center frequency or the reference level, go to the settings menu on the right.

#### Alarm Console: New alarm tab showing current suggestion events now has the 'Automatically remove cleared alarms' option enabled by default [ID_37855]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU10] - FR 10.4.1 -->

When you add a new alarm tab showing the current suggestion events, that tab will now have the *Automatically remove cleared alarms* option enabled by default.

This means that suggestion events will automatically disappear from the tab approximately 2 hours after they have been detected.

#### Settings: Default values of trend graph action settings have been changed [ID_37867]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU10] - FR 10.4.1 -->

In the *Settings* window, the default values of the following trend graph action settings have been changed:

| Setting | New default value |
|---------|-------------------|
| Right mouse button action on graph         | Select |
| Hotkey + left mouse button action on graph | Zoom   |

#### Service templates: Scrollbar added inside every tab of a service template card [ID_37882]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU10] - FR 10.4.1 -->

A number of enhancements have been made to the service template card, one of which is a scrollbar added inside every tab.

#### Alarm templates: Enhanced selection box in 'Anomaly alarm settings' window [ID_37899]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU10] - FR 10.4.1 -->

The selection box at the top of the *Anomaly alarm settings* window has now been made wider in order to better accommodate content in languages other than English.

### Fixes

#### A number of Automation issues have been fixed [ID_37674]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU10] - FR 10.4.1 -->

A number of issues have been fixed with regard to Automation:

- When, in the Automation app, you opened a script in an undocked card, it would not be possible to edit the name of the script.
- A *nullreference* exception could be thrown when an Automation script was deleted.
- Cube could leak memory each time you opened an Automation script in a new card.

#### Protocols & Templates: Function definitions would not be listed when you activated a functions file [ID_37754]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU10] - FR 10.4.1 -->

When, in the *Protocols & Templates* app, you activated a functions file, the activated function definitions would incorrectly not be listed. For this list to be displayed, you had to close the *Protocols & Templates* app and re-opened it again.

#### Visual Overview: Placeholder containing '[Elapsed Time]' would not be updated when the elapsed time had changed [ID_37756]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU10] - FR 10.4.1 -->

When the placeholder `[Elapsed Time]` was used inside another placeholder (e.g. `[Subtract:[Elapsed Time],[PreRoll]]`), the entire placeholder (e.g. `[Subtract:[Elapsed Time],[PreRoll]]`) would not be updated when the elapsed time had changed.

#### Pattern matching: Memory leak [ID_37771]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU10] - FR 10.4.1 -->

DataMiner Cube could start leaking memory when you opened trend graphs with pattern matching.

#### Alarm Console: Problem with hyperlinks that should be shown or hidden based on the value of a property [ID_37777]

<!-- MR 10.5.0 - FR 10.4.1 -->

When you had created a hyperlink that should only be shown when a particular property had a certain value, that hyperlink would never be shown when different types of objects (elements, services, views or alarms) had a property with a name identical to that of the property used in the filter.

#### Data Display: Problem when hovering over lite parameter controls in Skyline Black theme [ID_37814]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU10] - FR 10.4.1 -->

When DataMiner Cube was using the *Skyline Black* theme, lite parameter controls would become unreadable when you hovered over them.

#### Visual Overview: URLs that did not link to a DataMiner web apps would incorrectly get a connection ticket [ID_37822]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU10] - FR 10.4.1 -->

When the URL specified in a shape data item of type *Link* did not link to a DataMiner web app, but contained a keyword that could be interpreted as a keyword of a DataMiner web app, a connection ticket would incorrectly be added to that URL.

#### DataMiner Cube - System Center: Term 'Client independent updates' replaced by 'Server independent client updates' [ID_37926]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU10] - FR 10.4.1 -->

In the *System settings > Manage client versions* section of *System Center*, the term *client independent updates* has been replaced by *server independent client updates*.
