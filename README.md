# Text-Clustering Using DBSCAN


nitial Processes: The libraries necessary for the problem were loaded. The dataset train had 8580 lines in sparse matrix format. The idea was to import the file and split the indices and value and use them to construct the sparse matrix.
Loading the file: A csr_read() function was created. This function was used to read the given dataset only if the splitting up of the line gives even number of elements. After which value, pointer and Indices array were created, similar to the build matrix function in the Activity data 3. The function then takes in the input dataset as its input and returns us a Sparse matrix.
Normalizing the sparse matrix: The matrix from the previous step is then passed into the csr_idf function, similar to the one in the activity data 3, which returns a scaled matrix as dict. csr2normalize function normalizes the scaled matrix from the csr_idf function to give the normalized sparse matrix , that will be used for further analysis.
K-Means evaluation: Initially library version of Mini batch K Means was imported . This was used to obtain clusters > 100 which will be passed as input to the dbscan function. Here the argument was passed to produce 200 clusters. The cluster centers obtained were then stored in a list called points which will be passed as input for DBSCAN function, instead of the entire dataset, as DBSCAN performs poorly with high dimensional data and takes lots of time. This implementation avoids the curse of dimensionality.
DBSCAN algorithm: MyDBSCAN takes the points which is a list of cluster centers from the previous step, a threshold distance`eps`, and a required number of neighboring points `MinPts`.
It will return a list of cluster labels. The label -1 means noise, and then the clusters are numbered starting from 1.

Evaluation:
Silhouette score was used for the evaluation, the following were obtained
Eps=0.6, minpts=1 silhouette score -0.020
Eps =0.5 minpts= 1 silhouette score = -0.039
Eps = 0.51 minpts= 1 Silhouette score = -0.021
Eps = 0.52 minpts=1 Silhouette score = -0.019
Eps=0.53 Min pts =1 Silhouette Score = -0.013
Eps=0.33 Min pts =1 Silhouette Score = -0.024
Eps=0.53 Min pts =7 Silhouette Score = 0.004
Since Eps of 0.53 and Minpts of 1 gave a good result, that was used for the final analysis. It gave an NMI Score of 0.4245.
