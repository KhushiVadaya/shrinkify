# shrinkify
# Details of the project:
# 📦Image Compression using K-Means Clustering

This project implements an image compression algorithm using K-Means clustering. The goal is to reduce storage size while retaining visual quality by minimizing the number of unique colors in an image.

# 🚀 Project Overview:

Modern images contain thousands or millions of colors. Storing all of these colors increases file size.
Using K-Means, we can reduce the number of colors to just K representative colors, and replace each pixel with the closest centroid.

For example, compressing to 16 colors greatly reduces storage space while still producing an image that looks visually similar to the original.

# 🧠 Thought Process Behind the Project:
Problem Definition
I wanted to compress an image by reducing its color complexity without losing too much visual quality.
Observation
Each pixel has 3 features (R, G, B). These can be treated as points in a 3D space.
Idea
If we cluster similar pixels (colors), we can represent them with a single value — the centroid of that cluster.

Algorithm Choice
K-Means is perfect for this because:
It groups similar points based on distance.
We can choose exactly how many colors we want (value of K).
It is fast and scalable.

Implementation Strategy
Implement K-Means manually (instead of using libraries) to understand its internal working.
Write helper functions for:
Finding closest centroids
Updating centroids

Calculating cost (error)
Running multiple K-Means initializations
Run K-Means multiple times to avoid bad random initializations.

Final Step
Replace every original pixel with its cluster’s centroid and reshape the array back into an image.

# 🔧 How the K-Means Algorithm Works:
1. Initialization
Randomly select K pixels from the image as initial color centroids.

2. Assignment Step
For each pixel:
Compute its distance to all centroids
Assign it to the closest one
(Uses Euclidean distance)
3. Update Step
For each centroid:
Compute the average (mean) of all pixels assigned to it
This mean becomes the new centroid.

4. Convergence Check
Repeat steps 2–3 until:
Centroids stop changing (or change very little), OR
Maximum iterations reached.

5. Compression
Each pixel = replaced by its centroid → results in an image with only K distinct colors.

# 📊 Code Strcuture:
 find_closest_centroids(X, centroids)

Computes closest centroid for every pixel.
 compute_centroids(X, idx, K)

Recomputes centroids based on assignments.
 kMeans_algo(X, initial_centroids, max_iters)

Runs K-Means until convergence.
 run_KMeans(X, K)

Runs K-Means multiple times to reduce randomness.
 compress_image(image, K, max_iters, num_runs)

End-to-end compression pipeline.

# 🖼 Example Output:
Original image
Compressed image using 16 colors
Significant reduction in color space and size.
<img width="950" height="323" alt="image" src="https://github.com/user-attachments/assets/eb85a21d-ebb9-47ed-bfc6-03bb6de235f3" />


# 🏁 Results:
Successfully compresses images while maintaining visual quality.
Works for any RGB image.
Easily customizable: change K for higher/lower compression.
