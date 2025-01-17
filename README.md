
# <center>Bee(x)peRt</center>
Immersed in the sea of floating liters of beer within our minds, let's plunge into the intoxicating analysis of experts and their comparison with the "everyday" beer enthusiasts. But how to defines an expert among the customers ? Why should we truly trust what we label as expertise?

Picture a novice local brewery dreaming of its grand opening. Should it place its faith in the masses, in the opinions of the general populace, or should it exclusively lean towards the ratings of the acclaimed experts? In the cacophony of choices, should it navigate the path of a crowd-pleaser or trust the experts to turn its brew into the blockbuster highlight of a Saturday night among friends?

In this flavorful journey, we dissect the essence of expertise, question the reliability of expert ratings, ponder whether a brewery's destiny lies in the hands of the crowd or the discerning palates of insiders, and if it is worthy to pay for some experts advices. Join us in this spirited exploration, where the frothy symphony of data unfolds the secrets of brewing success.

## <center>About the Dataset</center>

This dataset consists beer reviews collected over period of 17 years (2001 to 2017) from two beer rating websites: BeerAdvocate (https://www.beeradvocate.com/) and RateBeer (https://www.ratebeer.com/). The dataset contain both textual and numerical data.

Following some analysis, the decision was made to merge the datasets from both platforms. This merging process aimed to obtain more robust and meaningful results in terms of expert and non-expert ratings. It was observed that combining both datasets reduces more the bias than considering each dataset in isolation. To mitigate potential biases introduced by the merger, a standardization procedure was implemented for the different rating systems used by the two websites.

To increase comparability, users on one website were linked with their counterparts on the other website, and a similar linkage process was applied to beers. This approach ensures a more equitable evaluation of ratings across the merged dataset, providing a foundation for reliable and unbiased analyses.


## <center>Who is an expert ?</center>
In this section we introduce our definition of experts, the ones that could be able to help making our beer successful.
### <center>Distribution of the number of ratings per user</center>
Let's dive into the satistics:


<div align="center">
  <img src="https://raw.githubusercontent.com/fpalmisa/ada-project-remontADA/81108e0145e72ff7a1ad0f8c87f5c60276f38499/assets/img/CCDF.png" alt="Plot Title">
</div>


The distribution has a heavy tail, indicating that there are numerous users who have posted only a few ratings, and conversely, a small number of users who are prolific raters. This observation motivates us to delve deeper into understanding the distinctions between these prolific raters and the rest of the user population. We'll pick up our experts from these figures.
### <center>Define who is a massive rater</center>

In order to separate people in two group, a definition of a massive rater, called from now an "expert" has to be found. The choice was made here to consider the number of ratings per year and aggregate scores from the past 3 years with the formula:

$S_{Y_j} = 2 \cdot R_{Y_{j}} + 0.5 \cdot R_{Y_{j-1}} + 0.25 \cdot R_{Y_{j-2}} + 0.1 \cdot R_{Y_{j-3}}$

, where $R_{Y_j}$ denotes the number of ratings for the year j and $S_{Y_j}$ is the score of the user for the year j.
The experts are then people from the 0.995 quantile of the score calculate previously (among those who have a non-zero score i.e active users).
These users only represent 0.5 % of active users and yet their influence on the ratings are huge since they account for huge part the final mean rating that will be displayed on the websites.

### <center>What an impact !</center>


<div align="center">
  <img src="https://raw.githubusercontent.com/fpalmisa/ada-project-remontADA/a72c07490fb8da00ab6ad8939e5b2e1a9b3964d3/assets/img/paleale.png" alt="Plot Title">
</div>

First of all, even if experts account only for 0.5% of the active they represent a big part in the ratings of the beers. There are even some years and styles for which they overtake non experts part. Thus, their voice really matter since they can make a huge difference for the final average rating displayed on websites.

By analyzing beers with at least 100 ratings per year, we observe that the difference in median ratings for the majority of them between experts and non-experts is very small. This reinforces the notion that while a discrepancy in ratings exists between the two parties, the overall trend remains largely consistent. It would be interesting to delve more deeply into this difference.

<div align="center">
  <img src="https://github.com/fpalmisa/ada-project-remontADA/assets/101518342/1de48878-a7cb-4b98-973f-041768d5c054" alt="Distribution 2017">
</div>


Plus we found that experts tend to rate beers that are less famous than those that are rated by casual users. Threfore, the fast and early sucess might depend a lot on experts tastes.

<div align="center">
  <img src="https://raw.githubusercontent.com/fpalmisa/ada-project-remontADA/1c4b4ab5cb9b68dec1e6dd1118cc98136ba803f7/assets/img/expert_proportion_since_begining.png" alt="Plot Title">
</div>

In general, a notable pattern emerges where experts initiate the rating trend, establishing an initial inclination. As the evaluation proceeds, non-experts increasingly contribute ratings, potentially outnumbering expert assessments. This indicates that experts set the initial tone, and non-experts play a significant role by adding a larger volume of assessments as the overall trend develops.

So it might be interesting to know if their ratings differentiate.
### How are they different ?
<div align="center">
  <img src="https://raw.githubusercontent.com/fpalmisa/ada-project-remontADA/1c4b4ab5cb9b68dec1e6dd1118cc98136ba803f7/assets/img/mean_ratings_experts_casuals.png" alt="Plot Title">
</div>

PLOT INTERACTIF!!!!!!!!!!!

It has been observed that experts tend to assess beers more critically than non-experts. However, despite these discernible distinctions, a common trend in ratings emerges, indicating that specific qualities are universally appreciated or disliked across both groups. Experts tend to be more severe than casual raters.
Moreover, it was remarked that experts rate beers that are less famous than beers rated by casual users.
A beer expert often has a more refined palate and extensive experience with various beer styles, ingredients, and brewing techniques. Their exposure allows them to detect subtle nuances, complexities, and flaws that a casual consumer might overlook. Additionally, experts may have a deeper understanding of the technical aspects of brewing, influencing their preferences and perceptions of taste. 
Also, analyzing the reviews and performing a sentiment analysis taught us that experts' reviews are significantly less positive than casual ones.
Then why should the breweries trust the experts while their perceptions seem to differentiate from the average consumer. It could seem paradoxical if the brewery wants to maximize its sales.

## Fabio Part

So far, it has been observed that experts tend to be stricter and more demanding in their ratings, which can clearly be explained by a certain professionalism and a palate that is more sensitive to the nuances of different beer tastes. Indeed, experts are accustomed to rating all types of beers, of different styles, and especially beers that are not necessarily well-known, thus contributing to having a potentially greater impact on the success of new blockbusters. So, when analyzing the opening of the brewery, there is a desire to take into account these sometimes slightly harsher and negative opinions, but which, in the long term, can certainly show all their advantages.
However, let's not forget that every expert was once a beginner and had to start at the very bottom of the ladder. That's why, when all is said and done, the question arises as to whether there aren't a few similarities in spite of everything.

So different but so similar? 

If we take a closer look at the different beers evaluated by experts and non-experts, we can still see some similarities. In fact, if we look at their distribution, we can see that despite the small bias still present between experts and non-experts, we can observe a certain similarity in the shape of the distributions. Admittedly, if we consider the number of ratings, these numbers are incomparable, but the distribution according to the years or the distribution according to the styles is quite similar for our two categories in their respective scales.

Let's just take the Pale Ale style as an example, which is one of the beers with a very low average rating. You had expect a very low score from most people, but a slight difference from the experts because of their experience and habits. However, over the years, it's always a style of beer that fails to convince either experts or non-experts in any significant way. In contrast, if we take the Witbier style as an example, we can see that the difference between the average score given by experts and non-experts remains very similar over the years. This trend is discernible for most of our styles, as well as for certain specific beers and their average rating. 

In the end, therefore, experts are different, but their tendencies are similar to that of non-experts. These observations are backed up by various interactive graphs, which clearly show this trend.

But why should one really care about the experts if they follow much the same trend as most people who pass judgment on beers? Sure, they're tougher, but do they really add value to the analysis? Let's take a look at the quality of their reviews to find out.



## ----------------------------------------------------------
## Strong or fruity words ?

In our exploration of beer reviews, nuanced results emerge as we focus on the distinctiveness and commonality in textual reviews among experts. The divergence in linguistic patterns is apparent, revealing a spectrum that spans from the intricately detailed lexicon of experts to the more commonplace expressions used by non-experts.

Examining the left pint of beer, representative of expert reviews, experts employ a vocabulary more in specificity, utilizing refined words and adjectives that contribute to a more intricate and nuanced analysis. The language employed by experts confirms what is observed during this beer's journey, reflecting a depth of understanding and a penchant for articulating subtle nuances in flavor, aroma, and overall beer characteristics.

In the right pint of beer, symbolic of non-expert reviews, presents a contrasting narrative. The language used by non-experts tends to be more basic in its use of adjectives. The choice of words in non-expert reviews again lacks the finesse and precision observed in the expert discourse.

In the context of creating a new brewery, these findings bear significance. The analyses conducted by experts, characterized by their complexity and precision, emerge as a valuable resource for informed decision-making. As we navigate the landscape of beer enthusiasts, there are advantages to placing greater trust in the reviews of experts, whose discerning language contributes to a more comprehensive understanding of the beer landscape.

In addition to examining the linguistic nuances, focus shifts to the quantitative aspect of beer reviews by analyzing the lengths of reviews provided by both experts and non-experts. There exists a significant difference in the mean lengths of reviews between the two groups. Furthermore, the investigation shows that non-experts tend to contribute longer reviews compared to their expert counterparts. This nuanced understanding of both qualitative and quantitative dimensions enriches comprehension of the diverse reviewing behaviors within the beer enthusiast community.

The conclusion is that we have more robust and complex reviews done by the experts. Even though non-experts make longer reviews, they are less complete. 
**This confirms what is observed during this sparkling adventure, indicating that relying on their analysis can help improve the beer's success, even if it means involving some costs. But trust in this! It's worth it.**

![BeerWordCloud](https://github.com/fpalmisa/ada-project-remontADA/assets/101518342/29cb2eab-c72c-49f5-923a-a230c75fd864)



## Sentiments Analysis to do 











### Contributions 
Fabio : 
Yannis : 
Vincent R. :
Vincent Roh : 
Alexi : 

### <center>Ethics !</center>

![ethic](https://github.com/fpalmisa/ada-project-remontADA/assets/101518342/e2f674a8-74d9-41a0-abda-ca1827f135f2)




In contemporary machine learning and applied data analysis projects like Beer Reviews Analysis, the evaluation of ethical risks is gaining importance. As designers of this kind of project, it is the responsibility to assess potential impacts and address them responsibly.

Focusing specifically on the Beer Analysis, one identifiable ethical risk involves influencing consumer choices. There are both indirect stakeholders, who are impacted by the system but do not directly interact with it (including the Public, Government, Environment, and Friends), and direct stakeholders, such as admins, end-users, or contractors, who have direct interactions with the system.

Taking the example of influencing consumer choices, considering only direct stakeholders, which are the customers. If the dataset is used to manipulate consumer choices by promoting certain beers over others through fake reviews or biased recommendations, it can be deceptive and unethical.

In this project, the aim is to use both datasets, incorporating the maximum number of reviews possible to minimize bias in consumer reviews and recommendations. Relying on only one dataset could introduce more bias into consumer choices. Hence, incorporating both datasets serves as an additional measure to mitigate bias and provide more robust and unbiased consumer advice.

### Credits : 

![Name](https://github.com/fpalmisa/ada-project-remontADA/assets/101518342/a3032a60-17de-478e-a0bc-90b9dd5bc6a7)

This project is done by Laaroussi Yannis, Palmisano Fabio, Roduit Vincent, Roh Vincent, Semiz Alexi for the course of Applied Data Analysis from EPFL (CS-401)
