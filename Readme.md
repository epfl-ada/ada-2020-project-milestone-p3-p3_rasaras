# EPFL - Applied Data Analysis (ADA)
## Project P3 milestone
Group : RasARas

Members : Azouz Rami, Fekih Selim, Mezghani Ayman

1) **Title** : Friendship and mobility
2) **Abstract** : The authors of Friendship and mobility paper try to study the impact of social networks on the mobility of humans. To achieve that, an intermediate step consists of predicting each user's home location using a discretizing method. The authors state that this method led to 85% accuracy using manual inspection. However, the provided dataset does not contain labeled locations which prevents us from measuring the accuracy of the proposed method. 
We propose another social network dataset with labeled locations to evaluate the claimed accuracy. Moreover, we aim at developing a machine learning model to predict users’ home locations.
The labeled locations offer us the possibility to conduct behavioural studies and answer questions such as where friends are most likely to meet.
3) **Research Questions** :
    - How accurate is the proposed earth discretization on another labeled dataset?
    - Where are people most likely to meet their friends?
    - Are there check-in patterns depending on country / region and time of the week?
    - Is it possible to use machine learning techniques to predict home locations using timestamped history of user check-ins?
    
4) **Proposed dataset** : 
    - Foursquare [dataset](https://sites.google.com/site/yangdingqi/home/foursquare-dataset) : Global-scale Check-in Dataset with User Social Networks which is used by the paper below :
        - Dingqi Yang, Bingqing Qu, Jie Yang, Philippe Cudre-Mauroux, Revisiting User Mobility and Social Relationships in LBSNs: A Hypergraph Embedding Approach, In Proc. of The Web Conference (WWW'19). May. 2019, San Francisco, USA. 
    - This dataset contains labeled locations (Bridge, medical center ...). One of these labels is "Home (Private)" . These labels will be very useful to proceed the methods. It also contains 
    - This dataset is also rich (up to 90,048,627 checkins by 2,733,324 users on 11,180,160 venues).
    - The dataset consists of three different files : 
        - Venues [`Venue ID`, `Latitude`, `Longitude`, `Venue category name`, `Country code`]
        - User check-ins [`User ID`, `Venue ID`, `UTC time`, `Timezone offset in minutes`]
        - Edges : indicate a friendship between two users
5) **Methods** :
    - Data Collection: 
        - Download the datasets (venues, user check-ins and edges).
        - Join the user check-ins and venues datasets to obtain a dataset with the following columns: [user_id, venue_id,local time, day_of_the_week, latitude_check_in, longitude_check_in, place, country].
    - Test the accuracy of the discretization proposed in the paper (using the new dataset):
        - Since our new dataset contains labels of checkins, we can use it to perform the discretization and try to find the homes of the users, then we test the accuracy of the method.
    - Friend meet-up locations: 
        - Find users (friends) who meet together. For example, if two users go to the same place and in a specified time window within each other, we consider that they met each other.
        - Analyze locations (restaurant, bar…) and time where friends frequently meet.
        - Analyze how far a person is willing to move / travel to meet with a friend.
    - Checkin-in patterns:
        - Find the distribution of the places where users usually check-in as a function of the day of the week (working day or week end), the local time (noon, evening …) and the location / region.
    - Exploration of ML techniques to find home locations:
        - Use clustering methods to find homes.
        - We are still unsure about the model to use (question for TA)

6) **Proposed timeline** :
Here is the proposed timeline with time estimates and assigned team members:
    - **Week 1 (28/11 - 04/12):**
        - Downloading the datasets (3h) (Selim)
        - Friend meet-up locations: data exploration (3h) (Selim)
        - Test the accuracy of the discretization proposed in the paper (using the new dataset) (6h) (Ayman)
        - Check-in patterns: data exploration and wrangling (8h) (Rami)
    - **Week 2 (05/12 - 11/12):**
        - Friend meet-up locations: wrangling (8h) (Selim)
        - Check-in patterns: analysis (6h) (Ayman)
        - Exploration of ML techniques to find home locations (7) (Rami)
    - **Week 3 (12/12 - 18/12):**
        - Friend meet-up locations: analysis (12h) (Ayman & Selim)
        - Exploration of ML techniques to find home locations ctd. (7) (Rami)
        - Data story / report (12h) (everyone)
    - **Week 4 (19/12 - 23/12):**
        - Short video (slides + recording + editing) (6h) (everyone)

7) **Organization within the team** :
Here is the organization within the team:
    - **Selim** will start by downloading the datasets. Then he will start the data exploration part of the Friend meet-up locations goal. In week 2, he will perform data wrangling for the same goal. In week 3, he will be joined by Ayman to perform the analysis.
    - **Rami** will perform data exploration and wrangling for the check-in patterns goal. Then, for the weeks 2 and 3 he will tackle the exploration of new methods for home localization using ML.
    - **Ayman** will test the accuracy of the discretization proposed in the paper using the new dataset. In week 2, he will take over the analysis of the check-in pattern. In week 3, he will join Selim in the analysis of the friend meet-up locations.
    - Each team member will report his findings for the report / data story individually. Then, they will collaborate to finalize it. Finally, they will collaborate in week 4 for the production of the video.

8) **Questions for TAs (optional)** :
    - About the additional ML method to use to predict homes, we are thinking about many different ideas and we would like to discuss:
        - Dirichlet mixture model for density estimation
        - Gaussian mixture model for density estimation
        - K-means model
        - Pure statistics

