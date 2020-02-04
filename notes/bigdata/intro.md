## Bigdata project essentials

Richard Hyda: ad2105@coventry.ac.uk
Available in Theta room for support **Fridays, 1pm-2pm**

#### Assessment (15 credits)

1. **Coursework** submission
    - [ ] a written report in PDF
    - [ ] a folder containing code + README codument containing instructions to run the code
    - [ ] combine the above in single ZIP file
1. **Portfolio** submission
   this should contain single document with evidence of successful project management
1. **VIVA** presentation
   marking schema available at moodle

#### Overall project description

We will be using 7 models. Data is presented on a grid spacing. For this project we'll be looking at O3 only. Grid is spaced at 0.1\* _longitude_ and _latitude_. This results **700x400** cover in Europe.

Data format: **NetCDF**, which is a standard format used in climate science. By using **DDC clustering algorithm** the **accuracy** of climate model ensembles can be **improved up 18%** (_Hyde and Angelov 2014_)

![What doeas the data look like?](https://i.gyazo.com/7c9e6563d8a904aacff15b760312c4ab.png)

![The Principles of the Project](https://i.gyazo.com/9af729846c80230a74cc669e430f9f58.png)

Big data problems

-   The provided data is a small subset of the overall project. Ozone only
-   Create 24 hours CBE by sequential processing takes many days
-   It's difficult to visualize the data

Big data solutions

-   sub-space the data
-   parallel process the grid locations
-   simplify the visuals

#### Given Radii values

O3 = 0.1257f; Lat = 0.0038f; Lon = 0.0021f

#### Requirements

-   [ ] use **big data techniques** to reduce processing time to <2 hours

-   [ ] create **requirements** document

-   [ ] create a simple **SMART** list

-   [ ] create PSEUDOCODE

-   [ ] create program flowchart

![Project steps](https://i.gyazo.com/e994d19164147e912da3e50778678d8e.png)

#### Definitions list

<dl>
	<dt>CBE</dt>
	<dd>cluster based ensemble</dd>
</dl>
