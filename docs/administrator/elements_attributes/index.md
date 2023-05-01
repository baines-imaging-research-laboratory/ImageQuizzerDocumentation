# Elements and attributes

The quiz file is set up with XML elements. Special attributes are associated with 
each element. The combination of elements and attributes enables the administrator to customize
how the Image Quizzer display will display the images and questions and in what order.

This section provides details for each element and attribute including available options and dependencies.
The following table provides an overview of the elements, subelements and attributes.


|Element|Sub-1|Sub-2|Sub-3|Sub-4|Attribute|
|--|--|--|--|--|--|
|Session|||||ROIColorFIle|
||||||RandomizePageGroups|
||||||ContourVisibility|
||||||EmailResultsTo|
|--|--|--|--|--|--|
||Page||||ID|
||||||Descriptor|
||||||LinkViews|
||||||Layout|
||||||PageGroup|
||||||AllowMultipleResponse|
||||||EnableSegmentEditor|
||||||SegmentRequiredOnAnyImage|
||||||MinMarkupLinesRequiredOnAnyImage|
||||||Loop|
|||Image|||ID|
||||||DicomRead|
||||||Type|
||||||LabelMapID|
||||||DisplayLabelMapID|
||||||RotateToAcquisition|
||||||ColorTable|
||||||Opacity|
||||||SegmentRequired|
||||||MinMarkupLinesRequired|
||||||InitialSliceOffset|
||||DefaultDestination|||
||||DefaultOrientation|||
||||Layer|||
||||Path|||
||||ROIs||ROIVisibilityCode|
|||||ROI||
|--|--|--|--|--|--|
|||QuestionSet|||ID|
||||||Descriptor|
||||Question||Type|
||||||Descriptor|
||||||Min|
||||||Max|
||||||GroupLayout|
|||||Option||






![In a nutshell](../assets/XML ElementsAndAttributes.jpg)