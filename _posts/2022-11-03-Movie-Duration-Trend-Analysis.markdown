---
title:  "Movie Duration Trend Analysis (using Netflix dataset)"
subtitle: "In this article, we would make simple research on whether or not movie duration decreasing. So, is the movie duration getting shorter now? Or is it otherwise? Let’s find out!"
author: "Aron Akhmad"
avatar: "img/authors/cat.jpeg"
image: "img/movie_duration_analysis/netflix.jpg"
date:   2022-11-03
---

Movies are a type of entertainment people love to have in their spare time. Over few decades, movies are getting more and more consumed as accessibility is much better and easier now. And as technology is getting better over time, the movie industry has grown its quality as well. However, the making process is getting much more complex either. Would the more difficult movie-making process impact the movie duration from then to now? Let's do some simple research on it!

First, load the Netflix CSV dataset and store its value in a data frame called durations_df. Print the first 5 data of durations_df using the head() function to get a glimpse of it.

<script src="https://gist.github.com/aronakhmad/a78eca349288c125bcbffa6c6063157f#file-data_loading-py"></script>
<img src="img/movie_duration_analysis/data_loading.png" width="100%" height="100%"/>

As you can see, there are a lot of columns on the dataset. We need to filter the columns to only those needed for analysis to make it more efficient. In this case, we only need 'title', 'country', 'genre', 'release_year', and 'duration'.

<script src="https://gist.github.com/aronakhmad/a78eca349288c125bcbffa6c6063157f#file-data_filtering-py"></script>
<img src="img/movie_duration_analysis/filtered_data.png" width="100%" height="100%"/>

To get a look at the spread of the data, we visualize each movie and its duration based on its release year. From the plot, we can see there are more movies created in recent decades and the durations get more diverse.

<script src="https://gist.github.com/aronakhmad/a78eca349288c125bcbffa6c6063157f#file-scatter_plot-py"></script>
<img src="img/movie_duration_analysis/scatter.png" width="100%" height="100%"/>

From the previous plot, we can see there are a lot of movies in recent decades and there are way more movies with shorter duration as well. This can be overrepresented. To get a more appropriate analysis, we need to dive deeper into it and see which genre movies with a duration of fewer than 60 minutes fall into.

<script src="https://gist.github.com/aronakhmad/a78eca349288c125bcbffa6c6063157f#file-short_movies-py"></script>
<img src="img/movie_duration_analysis/short_movies.png" width="100%" height="100%"/>

From the table shown above, we can see that movies that have a duration of fewer than 60 minutes fall into genres such as "Children", "Stand-Up", and "Documentaries". We should trim them out by marking them with different colors than the others. In this code below, we will color “Children” movies with red, “Stand-Up” movies with green, and “Documentaries” movies with blue. Meanwhile, the rest of the movies will be black.

<script src="https://gist.github.com/aronakhmad/a78eca349288c125bcbffa6c6063157f#file-color_labeling-py"></script>
<img src="img/movie_duration_analysis/color_labeling.png" width="100%" height="100%"/>

Since we’ve colored all the movies based on their genre, we can now re-plot our data and see what the new plot is like.

<script src="https://gist.github.com/aronakhmad/a78eca349288c125bcbffa6c6063157f#file-colored_scatter-py"></script>
<img src="img/movie_duration_analysis/colored_scatter.png" width="100%" height="100%"/>

You can see from the previous plot that movies with short duration in recent decades are mostly those that fall into "Children", "Stand-Up", and "Documentaries" categories. So now, we can count them out and continue our analysis with more accurate data in knowing whether movie duration in recent years is decreasing or not.

<script src="https://gist.github.com/aronakhmad/a78eca349288c125bcbffa6c6063157f#file-line_plot-py"></script>
<img src="img/movie_duration_analysis/line_plot.png" width="100%" height="100%"/>

We have plotted the data and from the plot, we can see that the movie duration was trending up from 1940 to the first quarter of the 1960s but then it fluctuates afterward, even in recent years. Thus, from the analysis we’ve made, we can conclude that the speculation or hypothesis saying that the movie duration is decreasing in recent years is false since the movie duration fluctuates each year.
