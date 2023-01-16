attribute: ROIColorFile="ColorFileName"

The administrator has the ability to assign specific roi names and colors that will appear as options
when the user is requested to do segmentation.

This is a .txt file and must be stored in the same folder as the study xml file.


Syntax for each line in this file:

```
roi# roi_name red green blue alpha
```

Example: A color file is assigned to a study for PI-Rads segmentation:

```
	|
	|_ObserverStudies
		|_PIRADS_SegmentationStudy.xml
		|_PiRadsStudy.txt
```


```
<Session ROIColorFile="PiRadsStudy">
	<Page>
		...
	</Page>
</Session>
```

```
PiRadsStudy.txt

1 PI-RADS_very_low 128 174 128 255
2 PI-RADS_low 241 214 145 255
3 PI-RADS_intermediate 177 122 101 255
4 PI-RADS_high 111 184 210 255
5 PI-RADS_very_high 191 2 34 255

```