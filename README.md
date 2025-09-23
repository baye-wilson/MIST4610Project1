# MIST4610Project1
## Team name and Members
Fantastic Four:
1) Tyler Meyer, [@tgm-UGA](https://github.com/tgm-UGA) 811444595
2) Baye Wilson, [@baye-wilson](https://github.com/baye-wilson) 811737308
3) Will Hooks, [@williamhooks912-byte](https://github.com/williamhooks912-byte) 811211871
4) Josh Tesar, [@joshtesar04](https://github.com/joshtesar04) 811846823
## Scenario Description
Our movie database provides a centralized system for managing and streamlining operations of the film industry. The database enables the tracking of essential components to movies including actors, budgets, sales, directors, and release dates. By consolidating all of this data into one database, we are able to simplify the process of extracting data and creating relationships between these different components. We is able to provide valuable insights for the film industry by observing patterns and trends that lead to box office success. Overall, our database aims to support the access to information for the film industry and foster better fact-based decision making.
## Data Model
<img width="929" height="412" alt="Screenshot 2025-09-21 at 3 11 12 PM" src="https://github.com/user-attachments/assets/8d41d124-2744-4f97-be75-e266f5680829" />

### Description of said Model
Our key fact table is the movies table; basically the actual films you’d see at the theater. Think of it like the center of the model. Just like how the credits roll at the end of a movie showing all the different people and pieces that came together, our movie table connects out to the different supporting entities like directors, actors, and sales.

Each movie also has sales tied directly to it like total box office and tickets sold, that information traces back to the single movie_id. 

We also ran into many-to-many cases. The obvious one is the cast. Instead of stuffing all the actors into the movies table (which would’ve made it messy and repetitive), we created a bridge table called movie_cast. That table links a movie to its actors using movie_id and actor_id. To keep things clean, actor details (like name and years acting) live in the separate actors table. This way, movie_cast just handles the connection, while actors holds the actual data about each person. 

By splitting it out like this, the model avoids redundancies, keeps the main movies table slim, and makes querying more efficient. It also gives us flexibility to now write queries that explore trends like “Do certain directors consistently have higher sales?” or “Which actors tend to appear in top grossing films?” The structure makes those insights possible without overloading any single table.


## Data Dictionary
<img width="652" height="275" alt="Screenshot 2025-09-22 at 12 35 20 PM" src="https://github.com/user-attachments/assets/ba2910de-3f50-4e84-bcb6-c572629a7044" />

<img width="654" height="414" alt="Screenshot 2025-09-22 at 11 51 42 AM" src="https://github.com/user-attachments/assets/28106eb2-80cf-4769-a692-88cfdfd9e8ae" />
<img width="658" height="272" alt="Screenshot 2025-09-22 at 11 51 54 AM" src="https://github.com/user-attachments/assets/47e6c67e-9565-4a26-ae12-4ae75747ef9e" />
<img width="658" height="283" alt="Screenshot 2025-09-22 at 11 52 02 AM" src="https://github.com/user-attachments/assets/7af81405-be5b-4bd0-b3dc-0f57f59355cb" />
<img width="664" height="270" alt="Screenshot 2025-09-22 at 11 52 12 AM" src="https://github.com/user-attachments/assets/290bc03a-91d5-4797-aece-809719ff0eb4" />



## Ten Queries
1. This query finds the average box office sales for each director and only includes directors whose movies have earned more than $10 million on average. It groups the data by director and calculates both the number of movies directed and the average total sales of those movies. The results are then ordered so the highest-earning directors appear first.
<img width="929" height="412" alt="image" src="https://github.com/user-attachments/assets/eb0e2a40-c811-4b41-bed6-7931f85e8b46" />

This query helps identify which directors consistently create financially successful films. By filtering for directors with an average above $10 million, managers or studios can easily see which directors are the most profitable.

2. This query lists all movies in the database in the order they were released, starting with the earliest.
<img width="929" height="412" alt="image" src="https://github.com/user-attachments/assets/08d95b10-8b5a-49e0-9846-76c2bbe483c9" />

This helps users quickly see the timeline of movie releases, which can be useful for analyzing trends or understanding how the catalog of films has developed over time.

3. This query finds actors who have appeared in at least two movies, showing how many films they acted in, their total box office sales, and the average tickets sold across those films.
<img width="929" height="412" alt="image" src="https://github.com/user-attachments/assets/d3d2fa4e-32f2-4a75-83a2-72df12f043d4" />

This helps identify which actors provide the most success for sales across multiple projects. Producers and studios can use this information to prioritize these higher earning actors in future films, ensuring stronger ticket sales and more of an audience appeal.

4. This query lists all actors along with how many years they’ve been acting, sorted so the most experienced actors appear first.
<img width="929" height="412" alt="image" src="https://github.com/user-attachments/assets/b7f95389-57f2-496d-9c9a-e1fc05546fe9" />
This allows managers or casting directors to quickly identify the most seasoned actors in the database.

5. This query compares each movie’s total box office sales with its production budget to calculate profit and return on investment (ROI).
<img width="929" height="412" alt="image" src="https://github.com/user-attachments/assets/a732947b-f189-48e6-8c38-2c162be74a26" />

This analysis highlights which films were the most financially efficient, not just in terms of revenue but also relative to how much they cost to make. Studios and investors can use this information to learn which types of films deliver the strongest returns and to guide future budgeting and production decisions.


6. This query shows director and actor pairs who have worked with eachother on a movie, showing how many films they worked on together and their combined total box office sales. The results are sorted so the most profitable partnerships appear at the top.
<img width="929" height="412" alt="image" src="https://github.com/user-attachments/assets/7a47f799-6c61-4c9e-bb28-c27dd460074f" />

This helps highlight the most successful collaborations between directors and actors. Studios can use this information to see which partnerships produce strong financial results, which may inform casting and directing choices in future projects.

7. This query shows all movies with production budgets greater than $200 million, listing their titles and budgets in descending order.
   <img width="929" height="412" alt="image" src="https://github.com/user-attachments/assets/8b0df179-0775-45b9-854c-ffdfd8a853ff" />
This helps identify the most expensive films in the database, which can be useful when comparing them to less highly budgeted films.

8. This query finds each actor with the movie they earned the most from. Then, it joins the tables together and uses a correlated subquery to determine the highest total sales for that actor. Only the movies that match this maximum sales value for each actor are returned, and the results are ordered from highest to lowest grossing movies.
<img width="606" height="558" alt="Screenshot 2025-09-22 at 6 48 40 PM" src="https://github.com/user-attachments/assets/31fe85f2-7ca4-4ec2-9eba-da97de892495" />

This might be useful for a manager looking to analyze high-performing movies with high-performing actors- big names bring in big audiences, and big audiences bring in big sales. Additionally, the ordered nature of the results are easy to interpret and apply. 

9. This query lists all titles, sales, budgets, and calculates the profit of movies that earned more at the box office than the average total sales of all of the movies included in the data. 
<img width="731" height="408" alt="Screenshot 2025-09-22 at 8 20 21 PM" src="https://github.com/user-attachments/assets/e000ed39-a6ed-4931-b085-a82e005cb8e6" />

This might be helpful to a manager who is looking to analyze how different above-average movies' perform in comparison to their budgets.

10. This query identifies directors whose movies have titles with more than one word in it. It shows the count of how many multi-word movie title each director has as well as the combined total sales of those movies. The results are grouped by directors and sorted so that the highest-earning director is first.  
 <img width="538" height="489" alt="Screenshot 2025-09-22 at 8 21 06 PM" src="https://github.com/user-attachments/assets/c9a43577-fe7f-446f-a46e-3cbdbba90b19" />
 
This query would be helpful for a manager who was looking to analyze the trends between multi-word movie titles and their performance. Additionally, a manager could identify trends a director has themselves, like a tendency to have multi-word movie titles perform well.
 




## Database Information
<img width="663" height="444" alt="Screenshot 2025-09-22 at 7 40 02 PM" src="https://github.com/user-attachments/assets/a223698e-98a3-43de-80cc-789048af3570" />

Name of the database: br_wah54338

All queries are bookmarked through stored procedures and can be called using this format: CALL TP_Qx(); where 'x' is the query number.
