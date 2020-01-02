## Continuous Development Plan (CDP)

<dl>
	<dt>Idea</dt>
	<dd>Why can't we use some of the Scrum parts to improve the learning?</dd>
	<dt>Goal</dt>
	<dd>Find the areas where I want improve, plan them and do the action</dd>
	<dt>Outcome</dt>
	<dd>Getting closer to the expertise of software development and engineering</dd>
</dl>

### Introduction
Most of the young developers get stuck at learning rapidly changing technologies. There are to many things in programming world to learn, but how to pick and learn it efficiency? For instance, if I want to learn React, first I must to know javascript, html, css etc. As a result, a learning of React becomes ineffective as you don't have fundamental skills. The answer is PLANNING.

This project will cover an approach to continuously improvement as a developer by splitting the tasks into managable parts similar to some of the Scrum techniques like Story-Mapping, prioritization etc.

Let's begin!

### The schema of the idea
![development schema](/images/cdp_schema.png)

### Table of contents
1. Plan the subjects you want to learn on the paper `Start`
1. Create a learning map `Create a map`
	* Introduction
	* Coloring the nodes
1. Find useful resources - `Resource backlog`
	* Introduction
	* Prefered resource types
	* Using excel template to track resources
1. Iteration based learning - `Iteration plan`
	* Creating the plan
	* Learning cycle
	* Definition of done
1. The drawbacks of CDP learning model


### 1. Plan the subjects you want to learn on the paper
It's important to understand what you want to learn and set a goal. There are to many things to remember to focus on. To have an image of what we want to learn, the best practise is to take a peace of paper and write everything down (mind-map it). This is important for the next step of planning of a detailed learning schema. You might use arrows to connect related things together. Start with a root node i.e. `Programming` or `Software development`. 

### 2. Create a learning map
> Learning map

![learning map example](/images/map_example.png)

##### Introduction
Now we need to create a full map of the things we want to learn. We are going to use the scrap paper of ideas we have just created. It's is a good practise to nest into small manageable parts. Usually the last element can be learned from a couple of articles within a period of 3 days.

> To achieve this, I suggest using https://draw.io website for drawing diagrams. Call the learning-map diagram `cdp.drawio`

##### Coloring the nodes
As from the example above, we can make use of coloring. Why not? :smile: You can make your own coloring agenda but main is this:

Big elements coloring:
- ![red](https://placehold.it/15/E9514C/000000?text=+) coloring the root and level 2 elements (because they are huge itself)
- ![sky blue](https://placehold.it/15/5BB3E4/000000?text=+) coloring the level 3 elements (because they are huge as well) ***optional***

Status coloring:
- ![white](https://placehold.it/15/F9F9F2/000000?text=+) no learning resources assigned
- ![yellow](https://placehold.it/15/ECEB72/000000?text=+) learning resources has been assigned `resource backlog`
- ![green](https://placehold.it/15/77E563/000000?text=+) learning is finished

### 3. Find useful resources

##### Introduction
Knowledge doesn't come from nowhere. That's why it is important to prepare the resources we are going to use for learning. The list of resources might change overtime time, that's why we call it *backlog*. One of the best ways to keep track easily is by using an **Excel sheet**. An example Resourse Backlog can be found in the file `cdp.xlsx`. 

##### Prefered resource types
- Books
- Videos
	- Youtube
	- LinkedIn learning
- Documentation websites
- Online learning websites like W3School, TutorialsPoint etc.
- Blog websites like medium.com
- Lecture slides

##### Using excel template to track resources

> Resources backlog

![resource backlog example](/images/resources_example.png)

The goal of the `resource backlog` is to store all learning material in one place with an option to keep track of progress and reference to a `learning map`.

Let's examine the columns of the table:
<dl>
	<dt>Iteration</dt>
	<dd>A reference to an iteration that can be found in iteration sheet. Iteration is a detailed plan of topics to learn in a given time</dd>
	<dt>Node title</dt>
	<dd>The title of the topic that the resource refers to. This also refers to a learning-map node. Once this is done, color that node Green</dd>
	<dt>Tree path</dt>
	<dd>Gives a path to the node in a learning-map starting from the root element and not including it (this makes the backlog shorter and less confusing)</dd>
	<dt>Depth</dt>
	<dd>An automatically calculated field by an excel formula (counts symbol / in the path). Depicts a selected node depth within the root node. Useful when prioritizing which topic to learn - pick the lowest element/node possible as it is essential to learn the node above</dd>
	<dt>Resource type</dt>
	<dd>Dropdown selection that gives you options mentioned in the Prefered Resource Types above. Gives a clue about the link website type</dd>
	<dt>Reference</dt>
	<dd>A link to a selected website described by other columns</dd>
	<dt>Learning state</dt>
	<dd>Dropdown selection that can be customized but the default one is: Selected, Reading resources, Making notes, Testing knowledge, Writing a program, Done </dd>
	<dt>Done</dt>
	<dd>Automatically filled field associated to the Learning State column. Once it is Done the column turns to Green background which helps to identify the progress. Otherwise, background is Red</dd>
</dl>

### 4. Iteration based learning

The idea might work without iterations but to get the most of it, it's wise to put yourself in a time box (*just like Scrum model does*). If you don't want to be timeboxed I still recommend you to create ***"Iterations"*** with an unlimited time as it helps you to manage the learning.

##### Creating the plan

First thing to remember - don't create plans upfront because it might change during the development of current plan. Consequently, you will waste your expencive time.
- Take some node as a branch and try to stick with it learning its children (if possible)
- Don't use high level nodes if you haven't learned children ones

##### Learning cycle

Simple: Reading resources, Making notes, Testing knowledge, Writing a program, Done.
> Check `The schema of the idea` if needed

You can make notes in numerious ways but I suggest using `.markdown` file type if you prefer taking them on the computer. Store them in `/notes` folder.

`Learning state` column will help you to track the status :wink:.

##### Definition of done (DoD)

An lastly, how do we know if the item is done heh? :roll_eyes:
Simple, by defining your own definition of done like:
- Notes have been taken?
- *Optional* Online tests/exercises passesed?
- Small program has been written?

If the answer to all of it is ![green](https://placehold.it/15/228B22/000000?text=+) YES, then DoD has been met and you can color the node in the `learning-map` with green background. After that go upwards that node.

### The drawbacks of CDP learning model
Nothing is perfect. There are some drawback I found:
- A preparation stage is time-consuming and looks to be scary but in the long time perspective you safe your time.
- Searching for valuable resources might be painful, but anyway you will have to find them at some point.
- Hard to understand the technique if you are not familiar with Scrum but still possible.
- The learning map might grow to a mess. For this I suggest you creating a couple of CDP projects
