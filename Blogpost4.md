After giving a lot of thought to what question I could ask a set of big data in my final portfolio for DHUM 73000 Data Visualization (Summer 2018) I decided to focus on something I really enjoy. One of the things I like best to do is go to a New York Public Theater Free Shakespeare in the Park performance at Delacorte Theater in Central Park. 

This is a whole day experience because unless you can afford to donate at least $500 to New York Public Theater, getting a free ticket involves going to Central Park early in the morning (I try to get there at 6 A.M. when the park opens) and waiting on line until tickets are handed out at noon. I take a blanket, a book, a laptop, food, drink and sunscreen and spend a pleasant morning on a patch of grass hopefully in the shade. This sounds relaxing, and so it is, but usually by the time I have my tickets in hand I’m stiff and achy from lying on the hard lawn (smarter people bring folding chairs), hot from the sun and ready to go home to shower and have a nap so as to be alert enough to enjoy the play, which usually starts around 7 P.M. the same day.

A nap is especially advisable if you are going to see King John. I have seen King John twice, in its full four-hour length, once at Delacorte Theater in Central Park and once in London at Shakespeare’s New Globe. Both times I wondered why someone chose that play. It has some good parts, but unless you know a lot about the Magna Carta of 1215 and the English constitutional crisis that ensued, you may find it hard, as I did, to follow the plot. I suspect that King John is usually staged only because it is by Shakespeare; if so, the logical thing would be to stage it once in a full cycle. To my surprise, when New York Public Theater announced in 1997 that it had produced all of Shakespeare’s 37 plays, King John had been staged twice. King John twice, and Antony and Cleopatra only once. This baffling choice made by New York Public Theater piqued my curiosity, so I set to visualizing some of its data to see what other unexpected trends might lie in store. 

I took data from the Wikipedia entry “List of Shakespeare in the Park productions at the Delacorte Theater” (2018) and used it to visualize 121 plays performed in 56 years of Free Shakespeare in the Park by building a colorful donut chart. I created a coherently color coded bar chart that indicates how many times in this series each of Shakespeare’s 37 plays was performed. I made a treemap that shows notable actors who appeared more and less frequently in Free Shakespeare in the Park productions from 1962 to 2018, and another that shows the directors who directed the plays. In the process of visualizing this data I was able to answer my research questions, feel satisfaction in successfully meeting the challenges Tableau Public and Github kept throwing at me, and enjoy making the creative choices a visualization requires. 

A way to visualize all the plays that have been performed in New York Public Theater’s Free Shakespeare in the Park cycles at Delacorte Theater in Central Park since 1962 in sequence and at the same time viewable all together presented a challenge to me. A long line of boxes or a bar chart representing 121 plays over 56 years disappearing into the right of the screen was not going to impact the viewer with the great volume of plays as would all the plays and years together. A better way to hit the viewer with the size and scope of Free Shakespeare in the Park, I thought, would be to tile boxes representing years, listing the plays performed in a given year inside each box. I sketched these boxes but they were not attractive to the eye. There was too much text in each, and I remembered that Michelle warned against crowding the visualization with too much information. Then I had a eureka moment. Donuts. A tiled donut for each year, with plays represented as colored segments. I could see it in my mind’s eye and could think of no more perfect way of visualizing the data I had at hand. 

A donut chart is really two pie charts of different sizes placed one on top of the other. The smaller one is the same color as the background (in my visualization, white) and sits at the center of the larger pie chart to create the illusion that the donut has a hole. To build my pie charts I followed steps clearly described by Erin Daugherty in her Advanced Charts Tutorial which I have adapted here to describe my process.

First, I created a Calculated Field named "CALC:0" and entered the number "0" in the text box. 

I dragged this new CALC: 0 variable to Rows and then dragged a second CALC:0 variable to Rows, so that I had two of the same data pills sitting side by side on the rows shelf.

I clicked the dropdown menu on the second CALC:0 and selected Dual Axis. By doing this I created a combination chart and changed my Marks Card shelf to have three panes, one controlling both circles, the other two controlling one circle independently.

I right clicked the right axis and selected Synchronize Axis.

I clicked on the middle marks card and changed the Mark Type from a circle to a pie.

I clicked on the bottom marks card, changed the color to white and made the size of this circle a bit smaller. I now had a donut!

I clicked on my pie marks card (the middle one) again and saw that I had a new option here: Angle. 

Now that I had my first donut set up, I dragged Year to Rows and found myself with a long string of 56 tiny donuts. I didn’t want to string the donuts but instead to tile them. As a first step in building my tiled view I created a filter of seven years by dragging Year onto Filter and selecting 1962 through 1968. Now I had a line of seven donuts side by side. I dragged Year to Label in the Marks shelf to show the year in numbers in the middle of each donut. I then dragged Play to Color and now each donut represented a year and its segments represented plays performed that year. 

I didn’t want anything to happen when you hover over the year label at the center of the donut, so I clicked on my third CALC:0 marks card then clicked on Tooltip and deleted all text. I did want information to pop up when you hover on the play segments, so I selected the second CALC:0 marks card and dragged Play and Director to Detail. I clicked on Tooltip and edited the text box so that it read 

Play
by ATTR(Author)
Directed by ATTR(Director)
  
Finally, I deleted the worksheet title by right clicking on the top of the page, selecting Edit Title and erasing all text. I renamed the worksheet “Performed 1962-68.” To give the donuts more space I changed the view from Standard to Entire View in the dropdown menu at the center top of the screen. Then I proceeded to duplicate the worksheet. 

In my duplicate copy I clicked on the Year filter, selected the next seven years, and renamed the worksheet “Performed 1969-75.” I did this repeatedly until I had eight worksheets with seven plays on each, and one worksheet with only one donut for 2018. I added some text to this last worksheet to summarize the content of the visualization and provide the dates of this year’s plays. Now I was ready to put worksheets together to make my tiled view. 

I created a dashboard and called it “FSP 1962-2018.” First, I changed its size to 1000 X 1400 and then dragged the eight donuts worksheets onto the dashboard in a horizontal stack. As I did this I had to keep adjusting the heights of the sheets so that they didn’t squish each other. I right clicked the top worksheet and added a title and a prompt to hover over the donuts for more information. Then I right clicked on each worksheet in turn and selected Format > Format Borders and removed all borders, shading and lines. I saved my project and published it on Tableau Public by clicking on the dropdown menu Server > Tableau Public > Save to Tableau Public As.

{% include plot7.html %}

The second visualization was a response to the query that prompted me to embark on this project. I wanted to know many times King John had been performed in Free Shakespeare in the Park and how the number of performances of King John compares to numbers of performances of Shakespeare’s other plays. In this case, because there were only 37 different Shakespeare plays, I could visualize them all in one bar chart. 

I listed the plays in alphabetical order from left to right on the x axis by dragging the Play dimension to Columns and put the number of records on the y axis by dragging the Number of Records measure to Rows. Here I immediately encountered two issues: the first was that there were too many different plays in my bar chart, and I wanted only to look at plays by Shakespeare. To resolve this I dragged the Author dimension into Filter and selected only Shakespeare. All plays not by Shakespeare promptly disappeared, except, to my surprise, Non Pasquale, which was a pop rewrite of Giovanni Ruffini’s Don Giovanni and definitely not by William Shakespeare.  I went to my data tab and found the error in my data file, where Non Pasquale was listed as written by Shakespeare. I went back to my data source and corrected the error, then select “refresh data” in Tableau on the shelf where the data sits and not from the dropdown menu under Data (I tried refreshing from the dropdown menu first and that didn`t work).  

The other issue I encountered was the number of records. I knew from looking at my data that Measure for Measure had not been performed 18 times. The play had 18 records because I had given it a record for each notable cast so as to be able to create my third visualization, which I discuss below. For the bar chart I needed to get rid of extra records, so I created another Filter with the Unique Key dimension. When I had cleaned the data I had given each performance a number and each record a unique key, so it was easy to select only the first record for each performance, and in this way get the real number of performances. After doing this I right clicked on the axis, selected Edit Axis and made the Range Fixed from 0-6. I changed the axis title from Number of Records to Number of Performances. 

I dragged the Play dimension onto Color in Marks, and the bars took on the same hues for each play as they have in the donuts chart. I was thrilled that they did this automatically (Tableau is so smart) because consistent color coding in a series of visualizations is really important, as it links one bar chart to the other and helps the viewer make the connections I want them to make. I hid the color card that had popped up on the right side of the screen by clicking on the downward arrow and selecting hide card, then changed the view from standard to entire view to make the visualization more spacious. 

I pulled the Year dimension onto Label in Marks and years of performances appeared on bars. Then I clicked on Label, then Font, and made the numbers black. This is looking pretty good, I thought. It is always good to remove all unnecessary information (quote Tufte or suchlike) so I clicked on the word “Play” above the columns and chose to hide field label for columns. Then I right-clicked on the title and changed it from “Sheet 15” to “Number of Times Performed” and added a short paragraph explaining what the bar chart represents. I renamed Number of records Number of performances by right clicking in the page on the y axis and selecting Edit Axis.

Because every production of a play is a unique creation, I added the director’s name to the text that pops up when you hover over a year. To do this, I edited the text square by clicking on Tooltip and deleting extra words and unnecessary information, leaving only

Play
Directed by ATTR(Director) 

It was not necessary to create a dashboard to house my second visualization, because it consisted of only one sheet.

{% include plot8.html %}

My third visualization provides information about notable cast in the 121 plays produced by New York Public Theater in Free Shakespeare in the Park. There have been some superstar actors on the Delacorte stage, including Dustin Hoffman, Morgan Freeman, Al Pacino and Meryl Streep. There have been some amazing directors too, and the third visualization goes on to show the number of times each of these directed plays. 

To visualize notable cast in Free Shakespeare in the Park Productions I chose to use a treemap because I wanted to see which notable cast had played most frequently on the Delacorte stage. To create a treemap I simply dragged Notable Cast into Columns and Number of Records into Rows, selected treemap from the Show Me tab on the right of the screen and changed the color scheme. The brunt of the work that went into creating the notable cast visualization took place much earlier, when I cleaned and organized the data in Excel, which I subsequently saved as .csv. 

To do this, and following Erin’s suggestion, I duplicated data in the data source so that each notable cast would have its own record and unique key. I had to do this because to be a record in Tableau each notable cast needed to have a row of its own (a row is a record) and a unique key. These unique keys had to be listed in a vertical column in much the same way Excel or Access create keys. Therefore, if there were four notable cast in one play, that play needed four records and four unique keys. In the first row of my .csv file I defined the columns I wanted in Tableau by separating these with commas. I called these

Unique_key,Show_code,Year,Play,Director,Notable_Cast,Author

I created each unique key by copying and pasting the information for all the other columns (except Author) and replacing commas with dashes, so that each unique key contained the show code. This inclusion of the show code in the unique key proved important for filtering out duplicate records belonging to one play when creating the bar chart. I was quite amazed that Tableau made beautiful sense of the strings of data I fed it, but at the same time I was aware that the ease with which I created the treemaps is thanks to my having started with a good clean data set. My treemaps prove true the words of Edward R. Tufte when he says that, “statistical graphics, just like statistical calculations, are only as good as what goes into them” (The Visual Display of Quantitative Information, 15). 

My treemaps are effective and aesthetically pleasing after the donuts chart and the bar chart whose curves and towers contrast with the treemaps’ squares. However, I’m not totally happy with the way my visualization of Notable Cast and directors turned out because I couldn’t figure out how to list multiple plays in Detail or Tooltip; when there is more than one record associated with a notable cast or director Tableau inserts an asterisk. There is a way around this but it looks tricky and frankly, I ran out of time.

To compromise, I dragged Number of Records to Tooltip, which I edited so that it reads

Notable_Cast
acted in SUM(Number of Records) play(s)

This is not entirely satisfactory because my idea was to say which plays the actors acted in and in which years. I had the same issue with the directors’ treemap, and solved it the same way, writing

Director
directed SUM(Number of Records) play(s)

I created another dashboard and dragged the Notable Cast and Directors sheets into it, one on top of the other. I selected Entire View, got rid of borders in Format > Format Borders and saved my project. I was ready to publish my work on Github.   

{% include plot9.html %}

