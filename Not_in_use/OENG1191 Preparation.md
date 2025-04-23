---
title: Recent Notes
draft: true
---
# Course Timeline


>Week 1 start on 3 March

### Week 1 Autodesk Revit
Support **Assignment 1**
- Familiarisation
- Basic Modelling Part 1
### Week 2 Autodesk Revit
Support **Assignment 1**
- Basic Modelling Part 2
- Schedule
### Week 3 Autodesk Revit
Support **Assignment 1**
- Phases
- Sheets
### Week 4 Autodesk Revit
Support **Assignment 1**
- Family
- Dynamo Façade
### Week 5 Autodesk Robot Structural Analysis
Support **Assignment 2**
- Interface
- Basic Modelling
- Load
### Week 6 Autodesk Robot Structural Analysis
Support **Assignment 2**
- Visualisation
- RC Design

>Assignment 1 Due
### Week 7 Revizto
Support **Assignment 2**
- Issue Tracker
- Clash detection
### Week 8 Autodesk Navisworks Manage

Support **Assignment 3**
- Basics
- Clash detection
### Week 9 Autodesk Navisworks Manage
Support **Assignment 3**
- Time liner
- Animator
### Week 10 Autodesk Revit
Support **Assignment 3**
- Dynamo Calculation*  

>Assignment 2 Due
### Week 11 Unity Engine
Support **Assignment 3**
### Week 12 Unity Engine
Support **Assignment 3**

>Assignment 3 Due on week 14


# Useful links

https://www.autodesk.com.cn/support/technical/article/caas/sfdcarticles/sfdcarticles/CHS/The-path-to-RSA-msi-cannot-be-found-while-opening-steel-connection-Robot-Strutural-Analysis-2025.html


https://help.revizto.com/hc/en-us/articles/5674354336911-Publishing-Revit-projects-to-Revizto#h_01GFBKH7ESRHGF58C9REEF6SP5


# Assignment 2


**CLICK HERE TO DOWNLOAD THE REQUIRED FILES**

**Assignment Nature:** Individual Assignment
**Weighting:** 30%
**Overview of Assignment**
This assignment assesses your structure modelling, analysis, as well as project coordination skills underpinned by BIM. This assignment comprises three parts. Complete the following tasks for each part:
**Assignment 2 Part 1 Robot Modelling:**
1. Read the provided structural design drawings and use **Autodesk Robot Structural Analysis** to create a BIM structural model. This model should successfully pass the static analysis without any warnings. (Due to software limitations, Use American design codes.)
2. Define and apply _dead, live, and wind loads_, then create a _seismic analysis_. Manually combines all loads into a combination name as _Assignment2Loads_.
3. Print the following image from Results: diagram and Results: map in PDF format: 
    1. XXX
4. Perform _Required reinforcement of RC Beams/Columns_ on all beams and columns under ULS case _Assignment2Loads_. Configure the result table in the _General_ tab to display only columns _Section_, _Design case ULS_ and _Remarks._ Print the table as a PDF named _Calculation.pdf_.
5. Resolve issues by increasing the section size, only for affected components, as taught in class.
6. Generate drawings for all beams and save them as _Drawing_Beams.pdf_.
7. Generate drawings for all columns. Take a screenshot of any issue warnings and save it as _Column_issue.jpg_. Resolve issues by increasing the section size, only for affected components, as taught in class. After resolving the issues, regenerate the final drawings and save them as _Drawing_Columns.pdf_. 
8. Generate drawings for all footingss and save them as _Drawing_Footings.pdf_.
9. Generate drawings for all slabs level by level and save them as _Drawing_Slabs_GF.pdf_, etc.
10. Save the model with your name and student number as _NAME_sxxxxxxx.rtd_
11. Zip all generated files and model files into one file and name it _Part1.zip._
**Assignment 2 Part 2 Revizto local project:*
1. Create a local project in Revizto and name it with your student number.
2. Upload your _Drawing_Beams.pdf_ from part 1 into the Revizto project.
3. Open **XXXXX.rvt** in Revit and publish the project to Revizto (link to the project you created). 
4. In Revizto, use the measure tools to identify three locations where the clear height is less than 3 meters. Create an issue for each location with measurements, set the issue priority to _Major_, and set the deadline to _the same weekday of the following week from the creation date_.
5. Create the following _Search Sets_:
    1. XXX
6. Create the following _Appearance Templates_:
    2. XXX
7. Export the Revizto project to EXE and name the file _Part2.zip._
**Assignment 2 Part 3 Revizto cloud project:**
This cloud project consists of five levels, each student in a group responsible for one level. **Please discuss with your group members** to allocate the levels accordingly. There is no variation in difficulty between the levels.
1. Open your group Revizto cloud project.
2. In Revit, open the project file you have been allocated. Change the existing sheet name to your student number then publish the project to Revizto (link to the group cloud project). 
3. In Revizto, create the following _Search Sets_:
    1. XXX
    2. XXX
4. In clash automation, perform a clash test between the above Search Sets. Sync the clashes to the issue tracker.
5. Select the clash item from your Revit file, then use the switchback to Revit function. Create an issue showing the item in Revit from the _Revizto Isometric_ view.


## Robot
The total nominal shear strength $V_n$ is given by:

# $V_n = V_c + V_s$

- $V_n​$ = Nominal shear strength
- $V_c​$ = Shear strength provided by concrete
- $V_s$​ = Shear strength provided by shear reinforcement (stirrups)

# Assignment 2 Note


- 两种层高
- 两种柱子尺寸
- 一层柱子更多
- 两种梁尺寸

### 荷载：
Ground:
![[Pasted image 20250227124819.png]]

1. Self Weight
2. Tile Flooring
	1. GF
	2. -2
3. Timber flooring
	1. 1f 2f
	2. -1.5
4. Kitchen
	1. 1f 后四
	2. -5
5. Dining area
	1. if 前4
	2. -2.5
6. Office
	1. Lv1 lv2
	2. -2.2
7. Public Area
	1. GF 1F
	2. surface
	3. -1.5
8. Restricted Area
	1. 2F
	2. surface
	3. -1.2
9. Roof
	18. -3.5
10. Roof Live
	1. -1
11. Wall
	1. -20
	2. -10 on parapet

![[Pasted image 20250227132012.png]]
Standard seismic



### Slab Calculation Options
![[Pasted image 20250227132917.png]]
![[Pasted image 20250227133006.png]]
![[Pasted image 20250227133023.png]]