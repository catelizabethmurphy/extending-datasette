# extending datasette — cat murphy, feb. 10

### admissions data

**what do you notice about the map? what do the pins actually represent?**

the highlighted pins here represent the volume of data at each point, not anything specifially about the data itself. the larger the number, the more alarming the color (yellow vs. green vs. orange, etc.). so, a pin that says 100 actually represents 10 pins that each say 10. each "10" pin represents a high school — specifically, 10 years of available admissions data for that high school. once you click on an individual high school, a spiral of blue pinpoints emerges to show the number of datapoints connected to that location. it doesn't appear that you can actually explore that data, though — at least not from the map itself. that's actually super annoying and lowkey stupid. just saying.

**admissions apps ideas**

i faceted for public high schools and then checked out a few individual schools and noticed that applications have increased at almost every high school over the last 10 years — i mean, basically across the board. 

my proposal is an app that allows you to see, in various ways, `how popular your maryland public school is. 

im assuming in this context that im making this app for a maryland audience. so, first, i would want a searchable/sortable table that would list every public school and redirect you to a page showing school-specific stats for each school. by this i mean a graph showing trends in application #s and acceptance rates year over year. i would also want to show how it compares to the state and to the county, and i would want to include the school enrollment rates and state rankings as well (though that would require additional data collection).

from a journalistic perspective, though, the real question is why these numbers are increasing. obviously, there are a lot of factors here, many of which we’ll probably never know. however, it is often specific specialties or focuses or programs that set schools apart — so what are they? for example, BCC is known especially for its academics, which could help explain why its application numbers are so high. i would want to know what each school’s “thing” is, to whatever extent possible, so that i could not only map out where applications are going up but also the specialties those schools have. so, which sports schools are seeing increases in applications? which arts schools? which academically accomplished schools? how do they compare to one another? i’m not entirely sure how i would do this, to be honest. spike map, maybe? where height = increase and color = specialty? 

however, i also imagine an interactive cloropleth map based on the natural geographic boundaries of each school district — obviously, this would exclude the inherently specialty schools, but still. this map could be colored based on applications or acceptance rate, i haven’t really decided — i would need to explore the data more.

and i have no idea how i would accomplish this, but i would also like to have a map where you could enter your maryland address and it would tell you which high school you’re assigned to, what that school’s speciality is and how competitive it is/has been for out-of-district students, and then info about high schools are out-of-district but nearby.

### full text search

full-text search differs from filtering in that it applies across all columns rather than a single column and, unlike filters, it doesn’t rely on logic like equals, does not equal, starts with, etc. it simply looks for your search term anywhere in the data and displays matching rows. this is useful in cases where you are looking for *any* instances of a word or phrase in the data, not just in a specific column. 

this is different from semantic search, however, which uses embeddings to look for contextually similar phrases.