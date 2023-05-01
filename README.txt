Analysis of Mall Customers

1. Dataset overview
    Here we import the Mall_Customer.csv file and create the variable Customers
    Then we look at the data and se the various data types

2. Exploratory data analysis (EDA)
    In this part we begin to look at the dataset and analysis it from various different
    prespectives. First we create Distribution Plots and look at the following features
    "Age", "Annual Income (k$)", "Spending Score (1-100)". Here we can see the distribution
    of these various features. "Age" most people are younger than 50.  "Annual Income (k$)"
    most people earn less than 70k a year. "Spending Score (1-100)" most people spend between
    40-60.
    Then we look at the correlation of the Customers dataset. Here we see the following
    correlations # Spending score and Age have a negative correlation, so the older you 
    are the less you spend. Spending score and Annual income is a postivte correlation, 
    so the more you make the more you tend to spend.

    Then we look at various disturbutions of gender with the values of the dataset. We can
    see for the majority of the dataset that there is no major differece between the genders
    when it comes to the various features. However, "Spending Score (1-100)" seemed to have
    a differnce between male and female where female seemed to have a higher spending score
    than males.So I decide to look closer at the spending score. 

    Create a countplot too look the differnce between male and female customers. We can see
    that there are more females than males that are customers.

    We then replace gender Female and Male with 0 and 1 so we can work out spending score 
    we need to turn object/string into int

    Then we work out the spending score by creating two features male_S_score and female_S_score
    we then add the amount of 'Spending Score (1-100)' to the corresending gender for 
    each row of both gender and 'Spending Score (1-100)'

    Then we work out the mean of the female_S_score and male_S_score by S_score_mean

    We then create a barplot where we look at the S_score_mean and come to the conclusion 
    that there is no large differnce between male and female spedning scores. And that the
    only thing that rather impacts the speding score is the amount of females and males that
    spend money att the mall rather than females and males spending more money as a result
    of their gender. Therefore, I decided not to use 'Gender' in any clustering

3. Data Cleaning
    Here we find the amount of NAN values with isnull() there are 0 NAN values
    We then chose to drop ['CustomerID','Gender'] as 'Gender' has no role in any future clustering
    and CustomerID has no realtion to the data other than setting a value for each customer

4. Standardizing Data
    Here we Standardize the data to bring all features down (1 and 0) to a common scale without distorting
    any differece in each features range. We do this with the help of StanderdScaler() and
    call the Standardized data scaled_customers.

5. Relationship between factors
    Here we look at inital realtionships between the different factors. First between Age 
    and Spending score and second between 'Annual Income (k$) - Spending Score' and third
    Annual Income (K$) and Age. We use scatterplots to gain a insight as to how these
    features work in realtion to each other

6. Building the model 
    Here we create 3 different functions to build the model 
    1. def elbow_method(data): this function creates the elbow_method that is used to determin
    the optimal amount of clusters. This function works by declaring the variable cluster_sum
    that works as a list for the amount of clusters. In a range from 1-10 (optiaml clusters)
    we use K-means algorithm creating the variable k-means that then through .fit computes KMEAN
    where is trains the instance of clusters with the data where the cluser_sum is appended and then
    kmeans is .interia (where it measures how well a dataset was clustered by K-Mean). Then we
    do GRAPH VISUALIZATION where we add colours, titles, sizes and so forth

    2. def Kmeans_training(data, nummber_of_clusters):this Function is used for 
    Training K-Means Model on the Given Data. We create the variable kmeans_model where we
    have kmeans. Then we create the variable y_means that is the kmeans_model.fit where
    it computes the cluster centers and predict cluster index for each sample. Then we
    return the kmeans_model and y_means

    3. def cluster_visualization(data,nummber_of_clusters, y_means, xlabel, ylabel):
    first we do customizing of the graph. Then create the FUNCTION FOR EACH 
    CLUSTER COMPARSION. Here we have the nummber_of_clusters which we gfet from the
    elbow_method. we create a scatter plot the contains the data from the scaled_customers
    dataset which we are using to scatter with specific features along with the y_means
    being the optimal amount of clusters. We then create the label that is named in 'Clusters'
    with numbers based on the amount of clusters str(i+1). Then create the data_centroids
    using the kmeans_model and using cluster_centers_ that gives the Coordinates of cluster 
    centers. We then apply the same pricple as above in the centriods scatter. At the end we 
    apply the labels and fonts

7. Visualizing all the clusters 
    Here we then begin the Visualize the various clusters based on the same features we 
    used in part 5. We then create the variable X1 that contains the features that we want
    from the dataset scaled_customers(Standardized dataset). We then apply X1 to the 
    elbow_method to get the optimal number of clusters for the Dataset. 
    Then we use the Kmeans_training where we give the function the data and 
    number of clusters. so in this case Kmeans_training(X1, 5).
    Then we use cluster_visualization entering the data,nummber_of_clusters, 
    y_means, xlabel, ylabel. In this case cluster_visualization(X1, 5, y_means,
    'Annual Income (k$)', 'Spending Score (1-100)'). We then get the cluster of customers
    and can draw conclusion from that data. 
    We do the same as many times as we want lookign at different features against 
    different features. In our case we have X2 and X3, where we do the same thing above
    with different features and variables.

8. TSNE
    We then want to Visualize the dataset in 2D using t-sne.T-sne reduces high dimensions
     in 2d so we can see the dataset in 2 dimensions regardless of the nr of features. We
     first create the varible tsne and then set it equal to 2 dimensions of TSNE. we then 
     create customer_tsne where we fit the scaled_customers into an embedded space and 
     return that transformed output. We then run the elbow_method on customer_tsne to find
     optimal number of clusters. We then run customer_tsne and nummber_of_clusters through
     Kmeans_training. Lastly we create scatterplot to Visualize the 2 dimensional t-sne.

9. PCA
    Lastly we check to see if PCA helps the clustering through reduction in dimensions. 
    PCA is meant to help with the clustering by reducing "noise" in the datapoints. We 
    begin by setting n_compnents = 2 since we want to reduced dimensions we then create the
    variable customer_PCA where we fit the model with scaled_customers and apply the 
    dimensionality reduction on scaled_customers. We then use the elbow_method on 
    customer_PCA to get optimal number of clusters. We pass customer_PCA and 
    nummber_of_clusters through Kmeans_training. We then create the scatterplot manuelly
    instead of using cluster_visualization as we have no xlabel and ylabel in the 
    customer_PCA dataset

