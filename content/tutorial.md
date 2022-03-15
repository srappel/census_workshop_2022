---
layout: default
title: NHGIS Tutorial
nav_order: 6
---

<title></title>
<link href="https://cdnjs.cloudflare.com/ajax/libs/normalize/4.2.0/normalize.min.css" rel="stylesheet" />
<style type="text/css">#s-lg-content-26263830{margin:1em auto 10em; line-height:1.5em; font-size: 17px !important;}
			#s-lg-content-26263830 a{color:darkgoldenrod;}
			#s-lg-content-26263830 a:hover{background-color:#f7ff7f;}
			#s-lg-content-26263830 h1{margin:0; font-family:serif; font-size:4em;}
			#s-lg-content-26263830 h1 em{font-size: 0.75em;}
			#s-lg-content-26263830 h2{margin-top:1.5em; border-bottom:1px solid #cccccc; padding-bottom:0.5em;}
			#s-lg-content-26263830 ul{margin-bottom:2em;}
			#s-lg-content-26263830 li{margin-bottom:1em;}
			#s-lg-content-26263830 img{max-width: 800px; border:5px solid goldenrod; box-sizing:border-box; display:block; margin:2em auto;}
			#s-lg-content-26263830 #expert-instructions ol{margin-top:1em;}
			#s-lg-content-26263830 #expert-instructions{list-style-type:upper-roman;}
</style>
<h1>Using NHGIS Data<br />
<span style="font-size:48px;"><em>A Guide for the Modern Map-Minded Panther</em></span></h1>

<h2>Introduction, Part I</h2>

<p>This tutorial will show you how to use the free NHGIS service to obtain demographic data that you can use in GIS analysis and mapping.</p>

<p>You will:</p>

<ul>
	<li><a href="#filtering">search for</a> and <a href="#selecting">download</a> data from the NHGIS website;</li>
	<li><a href="#joining">work with your downloaded data</a> and turn it into a useable shapefile;</li>
	<li>and narrow your data down to a <a href="#specificpart">specific part</a> of the United States.</li>
</ul>

<p><strong>This tutorial was written with beginners in mind.</strong></p>

<h2>Introduction, Part II</h2>

<p>The <a href="https://nhgis.org/" target="_blank">National Historical Geographical Information System (NHGIS)</a>, a service provided by the Minnesota Population Center at the the University of Minnesota, is one of the best ways to access data from the Census Bureau. You likely want a shapefile that you can use for analysis in ArcGIS or QGIS. Data from NHGIS can also be adapted for web maps, interactive applications, and cartography.</p>

<p>Another advantage of NHGIS: It can be used to obtain data from as far back as the first U.S. Census in 1790. Not only does it provide the raw numbers, but you can also obtain shapefiles containing historical Census boundaries.</p>

<p>NHGIS can be intimidating to navigate. While the team behind it has done an excellent job balancing usability and comprehensiveness, demographic data is multifaceted and complex.</p>

<p>The goal of this tutorial will be to create a map of Milwaukee County (or some other county) showing the percentage of Black residents in each Census Tract using the most current data. The process for examining other locations, years, variables, and enumeration units will not be much different. Feel free to follow along by using the same data as our examples, or other data of your choosing. We will use ArcGIS Pro to work with the data we obtain.</p>

<p>Happy mapping!</p>

<h2 id="video">Quick Video Introduction</h2>
<p>Watch this quick (2:22) video providing an overview of the data extract process on NHGIS.</p>
<iframe style="display:block; margin:1em auto" width="560" height="315" src="https://www.youtube.com/embed/P1znKKm8vX4" frameborder="0" allowfullscreen></iframe>

<h2 id="filtering">Filtering Data</h2>

<p>You should have already set up an NHGIS profile as part of the workshop setup, but if not, please <a href="https://uma.pop.umn.edu/nhgis/user/new?return_url=https%3A%2F%2Fdata2.nhgis.org%2Fmain" target="_blank">do so now</a>.</p>

<p>On the <a href="https://nhgis.org/" target="_blank">NHGIS homepage</a>, click the <strong>Browse and Select Data</strong> link on the left menu. Alternatively, you may click on the <strong>Get Data</strong> button on the homepage or the <strong>Select Data</strong> link on the top navigation menu. You will see a page similar to this:</p>

<p><img alt="Data Finder page showing the available filters: Geographic Levels, Years, Topics, and Datasets." src="https://s3.amazonaws.com/libapps/accounts/112972/images/1-datafinder-new.png" /></p>

<p>These filters will allow us to tell NHGIS what specific data we want to add to our cart.</p>

<p>Select <strong>Geographic Levels</strong> to specify your enumeration unit. In our example, we want to obtain data on a Census Tract level.</p>

<p><img alt="Census Tract option is checked" src="https://s3.amazonaws.com/libapps/accounts/112972/images/2-geoglevel-censustract-new.png" /></p>

<p>Click on the green plus sign next to Census Tract. This will add that level to the Selected Geographic Level Filters area at the top of the page. Note that you <em>can</em> select as many units as you want, but this may add a layer of confusion to your process. Let's stick to Census Tract.</p>
	
<p>Click <strong>Submit</strong> at the bottom of the window.</p>

<p>A bunch of rows will now appear on the page. There are far too many to look through with such a limited filter; let&#39;s filter further.</p>

<p>Click on <strong>Years</strong>.</p>

<p>If you only want to look at U.S. Census data, the Decennial Years column will be your only concern; U.S. Census data is collected every ten years. Some options will be greyed out, but you can still select them. The greyed-out options are years for which data is not available given the other filters you&#39;ve selected. For example, since we chosen Census Tracts as our geographic level, every decennial year prior to 1910 is grey. This is because Census Tracts were never used before 1910!</p>

<p><img alt="Check boxes showing year options. 2010 is selected and there are options for 2000, 1990, 1989, etc. Years older than 1910 have a grey color" src="https://s3.amazonaws.com/libapps/accounts/112972/images/3-selectyear-new.png" /></p>

<p>Select the year(s) you&#39;re interested in, and hit <strong>Submit</strong>. We&#39;ll use the most current decennial census data, which is from the 2010 Census.</p>

<p>The rows under Select Data will update once more, but there are still a lot of records.</p>

<p>Click on <strong>Topics</strong> to narrow results even further.</p>

<p>Find the topic(s) you wish to map in the list that pops up. Many researchers are concerned with <em>Population</em> data, but there are other categories that can be accessed using the tabs on the left. Again, options may be greyed out if data for those topics cannot be obtained given the other filters you have selected.</p>

<p>We&#39;re interested in data about the Black population in Milwaukee County, so we will select <strong>race</strong> as our topic.</p>

<p><img alt="Showing the topics available under Race, Ethnicity, and Origins topic. 'Race' is selected." src="https://s3.amazonaws.com/libapps/accounts/112972/images/4-selecttopic-new.png" /></p>

<p>The first plus sign next to Race is the Table Topic Filter; the second is the Breakdown Filter. You may click the green question mark next to each of these terms at the top of the table to learn more. For the purposes of this tutorial, we will use Table Topic Filter. Click on the first plus sign and <strong>Submit</strong> once more.</p>

<p>We could select <strong>Datasets</strong> to narrow down our search even further, but it is not necessary considering the specificity of the other three filters. Take a look at the dataset filters anyway and notice how many are now unavailable. That's because of our previous filters for geography, year, and topic.</p>

<h2 id="selecting">Selecting &amp; Downloading Data</h2>

<p>Underneath the Apply Filters section is a table containing the results of your search. (You should be looking underneath the <strong>Source Tables</strong> tab, not Time Series Tables or GIS Boundary Files.) Chances are you will still have a significant amount of rows to search &mdash; and on multiple pages too!

<p>Many researchers want to map race data. If we click on the <strong>Popularity</strong> column heading, we can see that one row is much more popular than the others.</p>

<p><img alt="Sorting the results by popularity and showing that the most popular topics are Race, Hispanic or Latino Origin by Race, and variations on those topics." src="https://s3.amazonaws.com/libapps/accounts/112972/images/5-tablesort-new.png" /></p>

<p>It is likely this first row is the data we want. Confirm it by seeing what information the data table contains. Click on the table name, <strong>P3. Race</strong>, to open a window detailing the contents of this dataset.</p>

<p><img alt="Showing the details of a particular topic from the table. In this case, a lot of information about the table including variables and dataset metadata, information on available breakdowns and geographic levels are also shown." src="https://s3.amazonaws.com/libapps/accounts/112972/images/6-datatabledetails-new.png" /></p>

<p>Don&#39;t worry if most of this doesn&#39;t make sense to you. At the very least, we can determine from the Universe field that this table measures the entire population of a geographic level. &quot;Census Tract&quot; is one of those available geographic levels. Finally, it looks like &quot;Black or African American alone&quot; is one of the variables available to us. In other words, this dataset contains the total population of people who identify as Black or African American in each Census Tract. That is <em>exactly</em> what we&#39;re looking for.</p>

<p>Close the Data Table Details window to return to the filter search results. Click on the green plus sign on the left to add this data to our Data Cart. You can select multiple datasets if you would like &mdash; this could be useful if, for instance, you are not entirely certain that you&#39;ve selected the right dataset.</p>

<p>You may notice that we&#39;ve been using the term &quot;data table.&quot; That&#39;s because when you download data from NHGIS, it is delivered to you in the form of a table &mdash; the kind of thing you could open in Microsoft Excel or Google Sheets. It has no associated geographic coordinates, and it&#39;s definitely not a shapefile.</p>

<p>In the same area where you selected which dataset you want, click on the <strong>GIS FILES</strong> tab. If you&#39;ve provided adequate Geographic Levels and Years filters, the list of results will be mercifully short. In fact, our query only returns two boundary files!</p>

<p><img alt="Boundary files results showing only two options listed in the results tables." src="https://s3.amazonaws.com/libapps/accounts/112972/images/7-boundaryfiles-new.png" /></p>

<p>The boundary file that we are interested in is the <strong>2010 TIGER/Line +</strong>. This boundary file contains all Census Tract boundaries used in the 2010 U.S. Census. We&#39;ll add it to our Data Cart by clicking on the green plus sign. The cart will update accordingly.</p>

<p><img alt="Data cart information showing updates since we have selected a source table and a GIS file." src="https://s3.amazonaws.com/libapps/accounts/112972/images/8-datacart-new.png" /></p>

<p>NHGIS will provide a data table and boundary shapefile, and it will be our job to join them. Our data will include every Census Tract in the U.S., but we are only concerned with Milwaukee County &mdash; so we will need to trim the data too.</p>

<p>But we&#39;re not going to worry about any of that until we actually have our data. Click <strong>Continue</strong> in the Data Cart, then click on it again. Keep all of the options as they are by default. You may want to add a brief description of your project, so you can find this dataset later to modify or re-download. Click on <strong>Submit</strong> to be brought to your Extracts History.</p>

<p>Note that the status of your new extract is <em>queued</em>. It takes a little time for NHGIS to process a simple dataset like ours; more complicated extracts will, of course, take longer. Take a break for a few minutes. By default, NHGIS will send you an e-mail once your data is ready for download. Refresh the page until your extract&#39;s status is <em>completed</em>.</p>

<p><img alt="extracts view showing that the data is ready to download and is no longer pending." src="https://s3.amazonaws.com/libapps/accounts/112972/images/downloadready.png" /></p>

<p>You will need to download the <strong>table</strong> and <strong>gis</strong> as .ZIP files separately. Do so, and then extract them once they have finished. (If you&#39;re unable to extract your data from the .ZIP file, try <a href="http://www.7-zip.org/" target="_blank">7-Zip</a>.) Note that boundary shapefiles come in the form of a .ZIP file within another .ZIP file, and you&#39;ll need to extract both.</p>

<p>If some time has passed and you still haven't received an e-mail to download your data, you can download the data from the AGSL's sharepoint site:

<p><a href="https://panthers.sharepoint.com/:f:/s/UWMLibraries/AGSL/Ehi5GkIs3atLtJScxZQAMewBWeLPn_ToOIC60cZ-uv1Y3Q?e=6gRrgY">Click here to download sample data.</a> (0.5 GB, compressed)

<h2 id="joining">Understanding Data &amp; Joining Tables in ArcGIS</h2>

<p>If you have ever taken a GIS course, this should be familiar ground for you. If not, no worries. The ability to easily perform joins in GIS software is one of the advantages of using NHGIS, and it&#39;s a big one.</p>

<p>First take a look at the table you downloaded. Along with the .CSV file containing the data itself, you received a codebook (.TXT file) in the same directory. Unfortunately, the columns in the data table you just downloaded are often not self-explanitory: for this project, there is no clearly labeled &quot;% Black or African American&quot; column. This codebook is a necessary part of understanding your data. Open it and take a look.</p>

<p>You can quickly glance at the Context Fields. What we&#39;re mostly interested in is the part of the document starting with &quot;Breakdown.&quot;</p>

<p><img alt="Inside our codebook" src="https://s3.amazonaws.com/libapps/accounts/113117/images/9-codebook.png" /></p>

<p>Our variable of interest, &quot;Black or African American alone,&quot; is associated with the column heading <strong>H7X003</strong>. Because we want to map the Black population as a percentage of the <em>total</em> population in a Census Tract, we should also know that <strong>H7X001</strong> is the column for the total population in a tract.</p>

<p><em><strong>Hint:</strong> Remember to check the Universe!</em></p>

<p>Take the time to note all of the columns that you will want to use.</p>

<p>Keep both the boundary file and data table you downloaded somewhere on your computer where you&#39;ll be able to find it later. Your downloads folder or desktop are good options.</p>

<p>It&#39;s time to open ArcGIS Pro. Note that what we&#39;ll be doing can be done in pretty much any GIS software, such as the free <a href="http://qgis.org/en/site/">QGIS</a>.</p>

<p>We&#39;ll work on a new, blank map template. Assign the project any name you want. Navigate to the <strong>Map</strong> tab. Click the <strong>Add Data</strong> button and select <strong>Data</strong>  to add both the .CSV table and shapefile you downloaded from NHGIS to your document.</p>

<p>This next part will require some patience. Your boundary shapefile contains boundaries from <em>the entire United States</em>, so ArcGIS may take a little while to render it all. If your computer is having difficulty processing so much data, you can temporarily pause map drawing on the bottom left corner of the map view.</p>

<p><img alt="Starting ArcGIS Pro and showing data added to the map view" src="https://s3.amazonaws.com/libapps/accounts/112972/images/10-startingarcmap-new.png" /></p>

<p>We need to associate the data in the .CSV data table with the boundaries in our shapefile. This will be done by <em>joining</em> the tables. In GIS, the term <em>join</em> has a very specific meaning. In our case, it involves finding a column that both our .CSV data table and our shapefile&#39;s attribute table have in common, and merging the two into one big table.</p>

<p>If you would like a refresher on joins, check out the ArcGIS documentation: <a href="https://pro.arcgis.com/en/pro-app/help/data/tables/joins-and-relates.htm" target="_blank">About joining and relating tables</a>.</p>

<p>Right click on one of the file names in the contents pane &mdash; in our example, <strong>US_tract_2010</strong> and <strong>nhgis0017_ds172_2010_tract.csv</strong> &mdash; and open the (attribute) table. Thoroughly examining the table of any data you download is good practice. Do you see which field we&#39;re going to use to join the tables?</p>

<p><img alt="Table view showing the column names of the tabular data along with the first couple dozen rows of data." src="https://s3.amazonaws.com/libapps/accounts/112972/images/11-tableview-new.png" /></p>

<p>NHGIS very conveniently includes a GISJOIN column in all of its data. In other words, they&#39;ve done a big part of the hard work for us! Right-click on the shapefile name (for us, <strong>US_tract_2010</strong>), hover over <strong>Joins and Relates</strong>, and click on <strong>Add Join</strong>.</p>

<p>For the <strong>Input Table</strong> field US_Tract_2010 should be selected. If it is not, you can use the drop-down menu to add it manually. Next set <strong>Input Join Field</strong> to GISJOIN using the drop-down menu. The <strong>Join Table</strong> drop-down should already have your data table selected, but if not, do that. Finally, the last field, <strong>Join Table Field</strong> asks which field you&#39;re going to base the join on &mdash; again, that would be GISJOIN. Your window should look something like this:</p>

<p><img alt="Join dialog showing the spatial layer 'US_tract_2010' as 'input table', GISJOIN selected as both the input join field and join table field, and the join table pointing to the CSV tabular data" src="https://s3.amazonaws.com/libapps/accounts/112972/images/12-joindialog-new.png" /></p>

<p>Open the attribute table for your boundary shapefile once more. Scroll all the way to the right. Do these column names look familiar? They should be the same ones you examined in the codebook earlier. Congratulations &mdash; all of your data is now in one convenient (and, frankly, huge) shapefile!</p>

<p><img alt="Attribute table after the join, showing the existing columns from the shapefile with new columns from the joined tabular data." src="https://s3.amazonaws.com/libapps/accounts/112972/images/13-joinedtable-new.png" /></p>

<p>If you want to make a map of the entire United States, you&#39;re pretty much ready to go. If not, we still have some work to do. Regardless, take some time to appreciate the fact that you can now, with very little effort, make a detailed thematic map of the <em>whole country</em>. And you could do it with <em>anything in the U.S. Census</em>. Hopefully you feel that all of the effort you put into getting here was worth it!</p>

<h2 id="specificpart">Mapping a Specific Part of the U.S.</h2>

<p>There are a few ways to trim your data so it only includes your area of interest. The easiest method uses <a href="https://en.wikipedia.org/wiki/Federal_Information_Processing_Standards" target="_blank">FIPS codes</a>, which are already included in NHGIS data.</p>

<p>Check out the data table for your shapefile. You will find two columns: one begins with STATEFP, the other with COUNTYFP. They will be followed by a number; in our case, this is 10, because we are using data from 2010. Each state and county in the United States has a unique combination if FIPS codes. A simple way to find the FIPS code for an area is to use the official U.S. Census website: <a href="https://www.census.gov/geo/reference/codes/cou.html" target="_blank">2010 FIPS Codes for Counties and County Equivalent Entities</a>. The FIPS code for Wisconsin is 55; for Milwaukee County, 079.</p>

<p>Click on the icon on the top left of the attribute table window, then select <strong>Select by Attributes</strong>. Alternatively, you can use <strong>Select by Attributes</strong> under the Map tab in the Selection group.</p>

<p><img alt="Table Options menu" src="https://s3.amazonaws.com/libapps/accounts/112972/images/14-tableoptions-new.png" /></p>

<p>This is where you will tell ArcGIS which data you want. Leave the Selection type as the default <strong>New selection</strong>. Click on the <strong>New expression</strong> button with the green + sign next to it. In first drop-down menu of the <strong>Where</strong> clause Find STATEFP10 &mdash; it may be preceded by your shapefile name &mdash; and select it. The second drop-down menu should be set to <strong>is equal</strong>. In the third drop-down menu, we&#39;re looking for Wisconsin&#39;s code, 55. Find it toward the bottom of the list and select it. Your WHERE statement in the expression box should now look like the image below.</p>

<p><img alt="ArcGIS expression example" src="https://s3.amazonaws.com/libapps/accounts/112972/images/expression.png" /></p>

<p>We are interested in all Census Tracts that have both the Wisconsin state FIPS code <em>and</em> the Milwaukee County FIPS code. This means our query will include the word <code>AND</code>, which means all results of our query must include both FIPS codes. In SQL, <code>AND</code> is an operator &mdash; something used to compare values in a query. For more information, see <a href="http://www.w3schools.com/sql/sql_and_or.asp">SQL AND &amp; OR Operators at W3Schools</a>.</p>

<p>Complete the second half of the query by clicking the <strong>Add clause</strong> button below the expression you just created. Leave the first drop-down with the value of <strong>And</strong>. Now use the same method above but with the COUNTYFP field instead, using the FIPS code 079. If you did it correctly, your final expression should look something like this:</p>

<p><img alt="ArcGIS expression example 2" src="https://s3.amazonaws.com/libapps/accounts/112972/images/expression2.png" /></p>

<p>Alternatively, you may use the <strong>SQL</strong> button to write an SQL query that will perform this task. The final statement should look something like this:</p>

<p><code>US_tract_2010.STATEFP10 = '55' And US_tract_2010.COUNTYFP10 = '079'</code></p>

<p>ArcGIS will read this query like instructions, in much the same way you are reading this tutorial. In plain English, what you have effectively told the software is: <em>select all of the records in the US_tract_2010 shapefile where the state FIPS code is 55 <strong>and</strong> the county FIPS code is 079</em>. If the state FIPS code for a Census Tract is 55, but the county FIPS code is <em>not</em> 079, that Tract will not be included.</p>

<p>Click <strong>Apply</strong>. It may difficult to see, but ArcGIS has <em>selected</em> the entirety of Milwaukee County. Zoom and pan your map to see for yourself.</p>

<p><img alt="Milwaukee County selected in ArcMap" src="https://s3.amazonaws.com/libapps/accounts/112972/images/15-milwaukeecountyselected-new.png" /></p>

<p>As you may notice, however, the rest of the U.S. is still present. Indeed, selecting alone does not isolate your data. Right-click on your shapefile name in the Table of Contents on the left, hover over <strong>Selection</strong>, and click on <strong>Make Layer From Selected Features</strong>. <em>Remember this option</em> &mdash; it will save you a lot of time and energy throughout your GIS career!</p>

<p>You should have a new layer listed on your Table of Contents; it will be called something like &quot;US_tract_2010 selection.&quot; Go ahead and remove your original shapefile and data table (right click them and select <strong>Remove</strong>), since all of our data is now concentrated in this brand new layer. Zoom in a bit if necessary; you will notice that you have isolated your area of interest!</p>

You could save this layer as it's own shapefile, or create new selections to repeat the process for the entire state or different counties.

<p><img alt="Milwaukee County isolated in ArcMap" src="https://s3.amazonaws.com/libapps/accounts/112972/images/16-milwaukeeisolated-new.png" /></p>

<h2 id="wheretogo">Where to Go From Here</h2>

<p>You have the data you need. The rest is in your hands. Symbolization, projection, ancilliary map elements &mdash; these are all things you will need to consider when constructing your final map. If you are enrolled in a GIS class, you will undoubtedly learn the skills to symbolize your map to your needs and liking.</p>

<p>Those new to all of this should definitely check out <a href="http://mapschool.io/" target="_blank">mapschool.io</a>. If ArcMap is your weapon of choice, reference the official documentation: <a href="https://pro.arcgis.com/en/pro-app/help/main/welcome-to-the-arcgis-pro-app-help.htm" target="_blank">Mapping and visualization in ArcGIS for Desktop</a>.</p>

<p><a href="http://axismaps.github.io/thematic-cartography/" target="_blank">Thematic Cartography</a> is a great read, as is <a href="http://uxblog.idvsolutions.com/2013/10/20-unrequested-map-tips-part-1.html" target="_blank">20 Unrequested Map Tips</a>. Those who struggle with projections should look at <a href="http://projectionwizard.org/" target="_blank">Projection Wizard</a> and <a href="http://www.radicalcartography.net/?projectionref" target="_blank">the projection reference at Radical Cartography</a>.</p>