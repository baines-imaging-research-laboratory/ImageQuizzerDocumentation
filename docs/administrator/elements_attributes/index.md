# Elements and attributes

The quiz file is set up with XML elements. Special attributes are associated with 
each element. The combinatin of elements and attributes enables the administrator to customize
how the Image Quizzer display will display the images and questions and in what order.

The following table defines the basic elements of the quiz.
Some of these elements have sub-elements. Each element and their associated
attributes have been described in detail in their respective sections in this documentation.

| Element | Description |
| ------- | ----------- |
| [Session](session/index.md) | The root of the script containing all elements of the quiz. |
| [Page](page/index.md) | What appears in the Slicer layout containing groups of images and question sets. |
| Image | An element that defines how and where an image is displayed. |
|QuestionSet | An element that contains a group of questions.|
| Question | An element that contains a group of options. |
| Option     | An individual item that forms part of the question. |