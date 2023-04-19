---
hide:
- toc
---
<!-- let javascript handle toc on left sidebar -->

# Examples

This section contains example scripts to help the administrator with quiz creation.

If you wish to use the scripts provided in the examples in a plug-n-play fashion, 
see the [instructions and links to the sample data](sample_data.md).

## Building your script

!!! warning

    When building your quiz, the administrator creates and makes changes to the original XML file.
    This is known throughout the documentation as the *master* quiz file.
    When the user starts a quiz session, a copy of this *master* quiz file, with the same name is placed in the user's results folder
    ready to record the session responses. This is known throughout the documentation as the *results* quiz file.

    After your initial run of the quiz, if you edit the master quiz XML file,
	**you must delete the copy of the quiz in the user's results folder** before your next run.
	Otherwise, your changes will not be recognized on the next run.

