# AL_Authors_QGIS



User Guide for Alabama Authors of the 19th and 20th century Literary Maps (Fall 2023- Spring 2024) 

Primary contributors: Corey McDaniels, Kevien Shelton, Shatadrayian Marshall

Organization’s GitHub: 

Introduction:

Hello! From the start of Fall 2023, the Alabama Authors of the 19th and 20th century have dedicated much time towards the literary map side project. Dr. Beverley Rilett has been a central proponent of guiding the progress of/work for this project while Corey McDaniels(MSCSSE), Kevien Shelton (BSCS), and Shatadrayian Marshall (MSDS) has spent these last semesters towards this direct development of the project. During our development/research cycle, we thought it would be useful to create an in-depth user guide for anyone interested in further developing or using our publicly available application. This user guide will detail all the work, software used, methodologies, sites, presentation materials, and tutorial links needed for replication. Additionally, it will be useful for recreating our steps in producing our materials. The user guide will provide the following sections:

Fall 2023

Neatline Public map

Methodology

Tips

Spring 2024 (2nd Semester)

Python Sorting Script

Favorites List 

A.I. Biographies excerpt 

QGIS 2nd map methodology 

Presentation Materials

Important Sources/Tutorials 







FALL 2023; Neatline Public Map 

When it comes to this initiative, there are two literary maps. The first one was developed in Fall 2023 which was developed by Neatline; a plugin that is used on Omeka, while the second is the QGIS(non-public) map. We will discuss the QGIS map later in this user guide, but for the moment, we will revisit what has been accomplished previously. To recreate this map you need to do the following. 

Login with your credentials to the Alabama Authors Website.

Then once you get to the admin side of things then you will click on the Neatline plugin on the left side (Circled in red)

	3. Once you click on this, you may click on the Interactive Literary Map of Alabama 	Exhibit

4. Once you click on this exhibit you will be brought to the exhibit itself. Seen below is a 	full screen representation of our map for example:



Here is a view of the map as it appears on the site as well:

For the sake of this user guide we will be primarily focusing on the Neatline exhibit version of the map to give thorough instructions on how to recreate something like what we created.

5. To create a county, you will need to “sketch a polygon” through Neatline’s editor 	option. You will first do this by clicking the add “New Record” blue button on the 	left side of the screen. Once you do such you will be presented with these options. 



Anatomy of the html script.	

<p><a href="https://alabamaauthors.org/items/show/533">Douglas Fields Bailey</a>&nbsp;- Education</p>

Link to Alabama Authors Page : 

Full name of the Author: Douglas Fields Bailey

What association to this County do they have: In this example Education



6. Once you select the Map button this is how you sketch the actual polygons for the 	counties or any type of geometry you wish. If it’s a triangle, square, pentagon, etc. 	Then you should choose the draw regular polygon option with the number of sites 	that are in that shape. However, if it is a more complicated structure, such as a 	county outline then you should choose the “Draw Polygon” option to sketch such. 

Style

7. As for the style tab, this is where you can select the color options of the polygon 	that you have created. The fill and stroke refer directly to how that polygon appears 	when you select it from the menu. 





8. It should be noted that the menu on the right in the beginning graphic of step 4, 	then you can go to that specific county in the map which will present the authors in 	a list, If you click on their name then it will directly take you to their Alabama 	Authors page. 

Tips:

Adhere by the Map’s Color spectrum template if possible. It is good to follow by a methodology for why the map appears as is. If more authors are added to this map, update or adjust the docx file as needed.

If polygons on the map need to be redrawn, the user does not have to start from the beginning of that county. They can instead opt for the modify geometry option on the map tab.

If further instructions or any clarification for this map is needed, then you can refer to the presentation materials section.   

Additional screenshots of progress:



Heat map implementation 



                         

 

The heat-like color palette implementation on the map is there to represent the number of authors that have connections to these counties in Alabama. The darker the color, the more authors in the county and the lighter the county, the fewer authors in the county. We also transitioned from using shades of red to shades of blue so that the map could be interpreted by those who are subject to color blindness, but it is still read the same way.



2nd Semester Methodology; QGIS map: 

As for the second semester there were multiple products on both the back end and the front end that were developed. Most of these were published to GitHub, here is my GitHub link and the link for Alabama Authors organization link.  The first was a python sorting script used to comb through a csv.

Python Sorting script

Present on my GitHub page and the Alabama authors GitHub page is a python file referred to as sorting.py. Pull from this repository by copying the GitHub link and pasting it to your local repository through visual studio code. Within the sorting.py file is two dictionaries that include all of the Alabama counties and then the names of all Alabama authors. This will be denoted by something like this:

County_list = [ ..] and authors_names_array=[..]

The important functions to look into this file would be these: 

def get_authors_by_county(csvData, county_name):

csvData = pd.read_csv('/Users/coreymcdaniels/Desktop/Al Authors Local /Al-authors/Spring Semester dataset 2.csv')

#authorU_columns = ['Unnamed: 2', 'Unnamed: 7','Unnamed: 9', 'Unnamed: 10']

filtered_csvData = csvData[csvData['Unnamed: 6'] == county_name] # this didn't work go back to original Unnamed 6

#maybe need to add another consideration for any catches of county association. i.e. unnamed 6, unnamed 7, unnamed 10

authors = filtered_csvData['Unnamed: 2'].tolist() 

if len(authors) == 0:#try this out 

print("There are no authors in the county", county_name)

else:

print("Authors in", county_name, ":", authors)

return authors

get_authors_by_county(county_data(), county_name)



author_name = input("Enter the author you would like to search for: ")

author_name = author_name.strip()



def get_counties_by_author(csvData, author_name):

csvData = pd.read_csv('/Users/coreymcdaniels/Desktop/Al Authors Local /Al-authors/Spring Semester dataset 2.csv')

#unnamed columns list comprehensions 

countyU_columns = ['Unnamed: 6', 'Unnamed: 7','Unnamed: 9', 'Unnamed: 10']

filtered_csvData = csvData[csvData['Unnamed: 2'] == author_name]

counties = filtered_csvData[countyU_columns].values.tolist() # got this to work now. 

if len(counties) == 0:

print("The author", author_name, "is not associated with any county.")

else:

print("Counties associated with", author_name, ":", counties)



return counties 

These functions are to sort through the counties and author information to return all authors related towards one another. Within the Sorting repository, there are other files that work with 3D visualizations, and csv datasets that retain all the information for 1,700 authors. Any files may be added to this repo as needed!

























































SPRING 2024

User Guide for Favorites List; 

User Manual Alabama Authors

My Researchers’ Notes

By: Shataydrian Marshall

Graduate Student, Samuel Ginn College of Engineering

Auburn University

Auburn, AL

Purpose

The purpose of the Alabama Author “My Researcher’s Note” is for the user to select Alabama Authors that they find the most interest in. The goal would be for an end user to highlight important information as they are reading about the authors. The end goal be to would allow them to save the information and export in an excel sheet or pdf of their choice. The feature would be a valuable functionality as it would save the user time so that they do not have to continuously search for the information, repetitively.

 

Supported Hardware and Software

Hardware

This section lists the type of devices that are compatible with the Alabama Authors My Researchers’ Note feature.

Desktop

Windows PCs

Mac Computers

Linux Computer

Laptop

Windows laptops

Mac Laptops

Linux Laptops

Tablet

Ipad

Windows Tables

Android Tablets

Mobile Device

Iphone (iOS)

Android Phones

Windows Phones





Software

This section lists the type of software that are compatible with the Alabama Authors My Researchers’ Note feature.

Operating Systems:

Windows

macOS

Linux distributions (e.g., Ubuntu, CentOS, Debian)

Web Browsers:

Google Chrome

Mozilla Firefox

Safari

Microsoft Edge

Web Server Software

Apache HTTP

Omeka

Programming Languages and Frameworks

HTML

CSS

JavaScript

React.js

Backend:

Node.js

Development Tools and IDEs

Visual Studio Code

Eclipse

 

How to

You will find below the landing page.   





On this page you have the option to do 1 of 4 actions:

 

Select “Choose file”

This will allow you to upload an already existing .csv file with previously selected Authors or Books from your local desktop.



 

Select the “Researchers’ Collection”

This button will take you to a page where you can begin your selection of authors or books. 



 

Next, click the My Researchers’ Note button

This will take you to this landing page: 

Select “Add” this will add the authors to the users’ curated list





 

 

Select “Export User List”

This button allows the user to export their list of chosen books or authors.

 



 

Select “Clear My List”

This will clear the list of Authors or Books 


 

References

Chatgpt 4







Author A.I. biographies (Kevien):

Although ChatGPT 3.5 can produce a pretty good biography, ChatGPT 4.0 is recommended for the most concise biography possible. Generating this biography, however, is very simple. You simply must copy the HTML data of the author, ask ChatGPT to “Put this into 4-5 sentences while only specifying Alabama information and insert [AUTHOR NAME]” then paste the HTML and run the prompt. This will then generate the biography and if it still needs adjustments, you can ask the A.I. to do whatever else is necessary.























QGIS methodology 

If you want to create a map that is similar to this one, there are a few steps that it would be wise to take. First is to find a dataset that already has a shape.file of all of US States. Usually within these you will find that the individual counties will be there. 

2) from this you will find if you use the select tool you can select out the counties that you desire. These are the counties that we used for our map basis. 

3) The way that the individual points were constructed was primarily through the use of CSV (UTF-8) comma delimited spreadsheets. I thought that it was best to assign each author an point on the map based on latitude and longitude coordinates. 

Adhere to the legend!

Introduction: QGIS is the chosen vehicle that we chose for this semester for the literary map. Within this map we have the same 153 authors from the Neatline map, but with additional distinctions that categorize authors. It includes the following categories: Education, Monuments, State symbology, Grave sites, Combined Author information, and Birthplaces. Additionally, there is information included about state memorabilia and monuments which is distinct from the original map. It is important to note that while this was what was accomplished during the semester, there is still much work to be done. Leaving it easily accessible for those who want to get involved in the project in the future.  

Publishing map methodology: It’s a relatively straightforward process to publish maps to the web. It simply requires the QGIS2Web plugin, the video that provides instructions for such is in the links section of the user guide under Publishing map to GitHub. The process should take at most 5-10 minutes to do so. Once that tutorial is completed, your completed uploaded files should look something very similar to this. 

In order to access your map in a browser setting, you will need to download all the files from the repository. That index.html file is the important one that will need to be opened through a browser. 

Once the index.html is opened in the browser the map will look something similar to this:



A video example of how the map will work when opened in your desired browser is in the github as the Zip file named as; 

Selected Counties

Legend that can toggle on and off based upon the layers of the map. This will be automatically generated once the map is published on the web. 













Presentation/symposium tips/templates:









IMPORTANT SOURCES & TUTORIALS

Dataset link for the counties.

https://www.census.gov/geographies/mapping-files/time-series/geo/cartographic-boundary.html



Video was extremely helpful for cutting out any counties that we might want or geographical boundaries for the United States. This is also available as a QGIS Plugin. This will mainly be used for Alabama!

Quite easy accessibility to label counties. In this example they are already labeled. 

 Photos linkage video



Important documentation Excerpts:





 



Plugins:

Quick Map Services; This can be downloaded directly from the Plugins tab in the top tile. 



Video to do so, also can add satellite imagery

Practically functions the same as having an open street map layer. 

*Sidenote* Some of the county label names aren't the most well centered. 

Literary mapping:







Image adding tutorial with georeferencing material with the additional of georeferencing:



*Sidenote* we can add the 1969 map as a background layer to the QGIS map. 

Coordinates for Author mapping:



Coordinates for the QGIS 3D model test:

In this example I wanted to try to map the geometry of the Vulcan statue in Bham. 

Coordinates 33°29′30.18″N 86°47′43.86″W /  33.4917167°N 86.7955167°W  / 33.4917167; -86.7955167



Changing symbology in QGIS: 



Creating lines that connect two points:



Hyperlinking to items:



Publishing map to GitHub:



Custom icons and symbols in QGIS:









