---
hide:
- toc
---
# Elements and attributes

The quiz file is set up with XML elements. Special attributes are associated with 
each element. The combination of elements and attributes enables the administrator to customize
how the Image Quizzer display will display the images and questions and in what order.

Following is a table giving an overview of the elements and attributes.
These are linked to the details describing the available options and dependencies.


!!! Note "Case Sensitive entries"

|Element|Sub-1|Sub-2|Sub-3|Sub-4|Attribute|
|--|--|--|--|--|--|
|[Session](session/index.md)|||||[ROIColorFIle](session/roi_colorfile.md)|
||||||[RandomizePageGroups](session/randomize_page_groups.md)|
||||||[ContourVisibility](session/contour_visibility.md)|
||||||[EmailResultsTo](session/email.md)|
|--|--|--|--|--|--|
||[Page](page/index.md)||||[ID](page/id.md)|
||||||[Descriptor](page/descriptor.md)|
||||||[LinkViews](page/link_views.md)|
||||||[Layout](page/layout.md)|
||||||[PageGroup](page/pagegroup.md)|
||||||[AllowMultipleResponse](page/allow_multiple_response.md)|
||||||[EnableSegmentEditor](page/enable_segment_editor.md)|
||||||[SegmentRequiredOnAnyImage](page/segment_required_on_any_image.md)|
||||||[MinMarkupLinesRequiredOnAnyImage](page/min_markuplines_required_on_any_image.md)|
||||||[Loop](page/loop.md)|
|||[Image](image/index.md)|||[ID](image/id.md)|
||||||[DicomRead](image/dicom_read.md)|
||||||[Type](image/type.md)|
||||||[LabelMapID](image/labelmap_id.md)|
||||||[DisplayLabelMapID](image/display_labelmap_id.md)|
||||||[RotateToAcquisition](image/rotate_to_acquisition.md)|
||||||[ColorTable](image/color_table.md)|
||||||[Opacity](image/opacity.md)|
||||||[SegmentRequired](image/segment_required.md)|
||||||[MinMarkupLinesRequired](image/min_markuplines_required.md)|
||||||[InitialSliceOffset](image/initial_slice_offset.md)|
||||[DefaultDestination](image/default_destination.md)|||
||||[DefaultOrientation](image/default_orientation.md)|||
||||[Layer](image/layer.md)|||
||||[Path](image/path.md)|||
||||[ROIs](image/rois/index.md)||[ROIVisibilityCode](image/rois/roi_visibility_code.md)|
|||||[ROI](image/rois/roi.md)||
|--|--|--|--|--|--|
|||[QuestionSet](questionset/index.md)|||[ID](questionset/id.md)|
||||||[Descriptor](questionset/descriptor.md)|
||||[Question](questionset/question/index.md)||[Type](questionset/question/type.md)|
||||||[Descriptor](questionset/question/descriptor.md)|
||||||[Min](questionset/question/min.md)|
||||||[Max](questionset/question/max.md)|
||||||[GroupLayout](questionset/question/group_layout.md)|
|||||[Option](questionset/question/option.md)||

