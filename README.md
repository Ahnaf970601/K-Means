# K Means
 
The K-means algorithm is a popular clustering method used to partition a set of observations into K clusters, where each observation belongs to the cluster with the nearest mean. The algorithm aims to find groupings in the data by minimizing the variance within each cluster, which is also referred to as the inertia or the within-cluster sum-of-squares criterion.



Initialization of Centroids: K-means starts by initializing K centroids. These can be chosen randomly from the data points, or by other initialization methods like k-means++. The centroids are the initial guesses for the centers of the clusters.
Assignment Step: In each iteration of the algorithm, every data point is assigned to the nearest centroid, forming K clusters. The “nearest” is usually defined using a distance measure, such as Euclidean distance. This step is sometimes called the “Expectation” step.
Update Step: Once all points are assigned to clusters, the centroids are recalculated as the mean of all points in each cluster. This step is also known as the “Maximization” step because it maximizes the likelihood of the data given the clusters.
Iteration: The assignment and update steps are repeated iteratively until the centroids no longer change significantly, indicating that the clusters are stable and the algorithm has converged.
Convergence: Ideally, the algorithm converges to a solution where the assignment of data points to clusters does not change from one iteration to the next. However, this solution may be a local minimum of the cost function, meaning that different initializations of centroids can lead to different results.
Random Initializations: To mitigate the risk of finding a poor local minimum, K-means is often run multiple times with different random initializations. The best clustering result — in terms of the lowest cost function value, which represents the within-cluster variance — is chosen.
This process of assignment and update is repeated until the centroids stabilize, ensuring that the data points are not changing clusters between iterations.

1.Closest Centroid


2. Computing centroid means

Computing the centroid means is a crucial step in the K-means algorithm. Once every point has been assigned to the nearest centroid, the next step is to recalculate the position of each centroid so it is located at the center of the points that were assigned to it. This process involves taking the average (mean) of all the points in each cluster for each dimension.

The mathematical formula to compute the new centroid​ for each cluster is:
Computing centroid means.This means for each cluster, you sum up all the coordinates of the points in that cluster and then divide by the number of points to find the mean location in each dimension.

3. Random Initialization

Random initialization is a key step in the K-means clustering algorithm, which directly affects the outcome and efficiency of the clustering process. The goal is to choose initial values for the centroids that will lead to convergence on an optimal solution, or at least a good enough solution, as K-means can get stuck in local minima.

There are different strategies for initializing centroids randomly, here are a few:

Simple Random Sampling:

Select k data points randomly from the dataset to serve as the initial centroids. This is straightforward but can sometimes result in poor convergence if the initial centroids are not well-distributed
Random Partition:

Assign each data point to a random cluster and then calculate the initial centroids of these clusters. This can be a better option because it ensures that each cluster has at least one point.
k-means++ Initialization:

This is a more sophisticated method for initializing centroids that aims to place them as far apart as possible.
The first centroid is chosen uniformly at random from the data points.
For each remaining centroid, the next centroid is chosen from the data points with probability proportional to the square of the distance to the nearest existing centroid.
Forgy Method:

Randomly choose k observations from the dataset and use these as the initial means. This is similar to simple random sampling but is a specific method by name.
Maximin Initialization:

Choose the first centroid randomly, and then for the next centroids, choose data points that maximize the minimum distance to the existing centroids.


4. Image compression

Image compression using K-means is a technique where the algorithm is used to reduce the number of distinct colors in an image. The reduced number of colors are the centroids of the clusters found by K-means, and every pixel in the image is assigned to the nearest centroid color. This process reduces the image file size because it limits the color palette to a manageable number, which simplifies the storage and potentially speeds up image processing tasks.



After finding the top 𝐾=16 =16 colors to represent the image, you can now assign each pixel position to its closest centroid using the find_closest_centroids function.

This allows you to represent the original image using the centroid assignments of each pixel.
Notice that you have significantly reduced the number of bits that are required to describe the image.
The original image required 24 bits (i.e. 8 bits x 3 channels in RGB encoding) for each one of the 128×128128×128 pixel locations, resulting in total size of 128×128×24=393,216128×128×24=393,216 bits.
The new representation requires some overhead storage in form of a dictionary of 16 colors, each of which require 24 bits, but the image itself then only requires 4 bits per pixel location.
The final number of bits used is therefore 16×24+128×128×4=65,92016×24+128×128×4=65,920 bits, which corresponds to compressing the original image by about a factor of 6.

Image compression




