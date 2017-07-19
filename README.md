Susan Fung
Project 2: Luther
July 14, 2017

Objective:
Predict sale price of a house in Seattle (98103).

Data:
Sold single-family homes from zillow.com from the previous 90 days. Data was accessed July 11, 2017. This filter resulted in 104 listings. Sites were scraped for features using Beautifulsoup4. Ultimately, 88 data points were used for this initial analysis, likely due to not handling missing data from individual sites. 

Feature Selection:
Number of bedrooms, bathrooms, square footage were obvious initial features to include. The year the house was built was also selected.

Cleaning Missing Data:
Not all listings are standardized in what information is included. Some listings included studios or foreclosures (even though filter was specifically for single-family homes) and therefore did not have bedrooms. Additionally some listings did not include year built. Data was filled in using mean of a column. However, it is noted that filling in missing data should have occurred after the data was split into train and test slices.

Algorithm:
Linear regression was performed on normalized training data.

Evaluation:
The model was evaluated by cross validation assessed for predictive value via R-squared value and MSE. 

Parameter Tuning:
The first model made use of all features that were available and resulted in an R-squareof 0.76 with MSE 5.2e10. While R-square was a good start, the MSE was quite high. The next model focused in on using only square footage as the correlation betweeen this feature and sold price was high, 0.88. Unfortunately with the small number of data points, these next models were unable to be generated using new training sets, so "new" test/train splits are done on the same dataset of 88 points. Regardless, using only 1 feature resulted in an improved R-square of 0.86. MSE was also reduced to 3.5e10. The third model was a variation on the second model where square footage was square-rooted. This was done to try to experiment on the idea that there exists a sold-price plataeu as square footage converges to some maximum value. Interestingly, the R-square of 0.74 was comparible to the original model as was the MSE at 4.2e10.

Further Improvement:
More features, such as days on the market, total size of lot, number of people who "favorite" a house listing, walkability scores (these may be included in the listing or can be merged from additional sources), etc, can be scraped assuming there are better features that will predict sold prices. Grouping houses by architecture style or binning year-built are also other ideas. Applying the existing models to a larger dataset will also be useful.  

