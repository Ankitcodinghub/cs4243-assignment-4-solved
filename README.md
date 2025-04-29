# cs4243-assignment-4-solved
**TO GET THIS SOLUTION VISIT:** [CS4243 Assignment 4 Solved](https://www.ankitcodinghub.com/product/cs4243-instructions-solved-4/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;113956&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS4243 Assignment 4 Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
This lab has four parts. For each part, implement the outlined functions in lab4.py and run them in the notebook lab4.ipynb. For the Q&amp;A in Part 4, write your answers directly into the notebook. Expected outputs are supplied as reference but your results need not match exactly.

Upload to LumiNUS your completed lab4.py and lab4.ipynb by zipping them into a file named AXXX1_AXXX2.zip, where AXXX is the student number of the group members. Submit one file per group. Missing files, incorrectly formatted code that does not run, etc. will be penalized.

Note: You are free to re-use functions in previous labs and use any NumPy or OpenCV functions, except the built-in functions for mean-shift e.g. cv2.meanShift. For k-means clustering, you can use KMeans from scikit-learn. Please do not import other high-level computer vision libraries. We provide default parameter values but you are free to adjust these.

Objective

(a)RGB Image (b) Detected Keypoints (c) Clustered Points (d) Lattice Model (e) Final Output

Figure 1: Overview of translation symmetry detection. From the original image (a), the detected keypoints (b) are clustered based on similar appearance (c). RANSAC is applied to find vector pairs representing the lattice structure (d) before scoring the proposals and generating the final lattice (e).

Part 1: Shi-Tomasi Keypoint Detection and Clustering (30%)

We cluster keypoints based on the appearance of a local patch of ℎ𝑝 × 𝑤𝑝 around the keypoint to find repeating patterns. Keypoints from the same cluster should be located at the same relative positions for a repeating pattern (see Fig 1c, 1d, the clustered keypoints appear at the fence grid crossing).

o Patch-wise keypoint detection: Given an image of size (ℎ, 𝑤) , divide the image into approximately 50×50 patches and apply keypoint detection to each patch individually. Your image should have 𝑃 ∙ 𝑄 patches, where 𝑃 ≈ (ℎ / 50) and 𝑄 ≈ (𝑤 / 50).

o Quality decay: 𝜌 thresholds the minimum acceptable quality for detected keypoints. For each patch, lower 𝜌 progressively by a factor 𝛾𝜌 &lt; 1. Stop lowering 𝜌 when 𝑁𝑝, a required number of keypoints for each patch, is found or when 𝜌 falls below some threshold 𝜏𝜌.

• cluster() the patches with mean-shift clustering with bandwidth ℎ to produce a coarse set of clusters 𝐶𝑖, 𝑖 = 1, … , 𝑁𝑐. To avoid 𝑁𝑐 becoming too large, e.g., 𝑁𝑐 &gt; 𝑁 / 3 , tune the bandwidth by gradually increasing ℎ by a factor 𝛾ℎ &gt; 1. Limiting the number of clusters ensures that resulting clusters are not too small with too few points per cluster.

• Refine the mean shift clusters with the following conditions:

o Discard small clusters, i.e. those with less than 𝜏1 points.

o Partition large clusters with more than 𝜏2 points by applying k-means, 𝐾 = 𝑁𝑖 / 𝜏2, where 𝑁𝑖 is the number of points in the 𝑖-th cluster.

Part 2: Lattice Model Proposals and Evaluations (20%)

For a cluster of similar keypoints, we can solve for a lattice model, i.e. after applying some global transformation, inlier keypoint should fall onto a uniformly spaced grid (see Figure 2a). The grid of the lattice model is defined by a starting point 𝑝𝑜 and its associated basis vector pair (𝑡1,𝑡2) (see yellow points in Figure 2a). Depending on the number of clusters present, many proposals will be generated. Use an appearance score (A-score) to evaluate the proposals. The A-score is the average per-pixel standard deviation among the aligned texels (see Figure 2c); it gives low scores to texels that are similar pixel-wise. We aim to find proposals with the lowest A-scores.

Figure 2: Overview of lattice model proposal. And proposal scoring.

• get_proposal()applies RANSAC to find the most suitable basis vector pair for each cluster. For each cluster 𝐶𝑖, 𝑖 = 1, … , 𝑁𝑐:

1. “Randomly” sample a triplet (denoted as yellow points in Figure 2a), with priority given to points close to each other. Denote the three points as {𝑎, 𝑏, 𝑐}. Define as point 𝑎 the point opposite the longest edge of the triangle formed by the three points.

𝑚1 𝑚2 𝑚3

𝑀 = [𝑚4 𝑚5 𝑚6]. To solve for M, use cv2.getAffineTransform .

0 0 1

2. Apply 𝑀 to transform the 𝑋 points in the cluster closest to 𝑎. Count the number of inliers (Figure 2a, red points) whose transformed coordinate falls within a threshold 𝜏𝑎 of an integer position (𝑖, 𝑗) on the lattice grid. Remaining points are labelled as outliers (Figure 2b, blue points), i.e. those which are either too far or do not sit on the grid.

3. Repeat Step 1-3 for 𝑁𝑎 times and return the triplet {𝑎, 𝑏, 𝑐} with the largest number of inliers.

• find_texels()forms a set of texels {𝑇𝑘,𝑘 = 1, … , 𝑛} of shape (𝑈, 𝑉) based on the inlier keypoint set and their associated integer positions. Each texel is defined by 3 or 4 inlier keypoints on the corners. You are provided code in lab4.ipynb to project the texels from the image space into uniform square patches. For each patch, we compute a perspective transformation and warp it with cv2.getPerspectiveTransform and cv2.warpPerspective (please be careful about the coordinate ordering of these functions). Normalize the intensity of texels so that they have a mean 0.0 and a standard deviation of 1.0 before the calculation of A-score.

• score_proposal()computes an appearance score for the texels of a proposal by measuring the standard deviation of the aligned pixels. For a set of 𝑛 texels, the score is defined as:

𝑈,𝑉

A-score 𝑢,𝑣 , … , 𝑇𝑘 , … , 𝑇𝐾 ,

𝑈 𝐾

where 𝑇𝑘,𝑘 = 1, … , 𝐾 are the texels and are the local pixel indices of the texel. The denominator weighs the score based on 𝑈 𝑉, the number of pixels in the warped texel; 𝐾 is the number of texels and std() is standard deviation function. In case of RGB texels, compute the Ascore for each channel and then compute an average on the three channels. Keep the 3 proposals with the lowest A-scores for further processing to generate the lattice.

Part 3: Generate Lattice (20%)

The proposals from Part 2 can be applied to capture the repetitive patterns to generate the lattice:

points from local maxima

Figure 3: Overview of lattice generation.

• template_match() estimates a template and performs template matching. The template is defined by a patch 𝑇 which is the smallest rectangle that encloses the corner coordinates {𝑎, 𝑏, 𝑐, 𝑑} of the proposal, where the point 𝑑 can be predicted from {𝑎, 𝑏, 𝑐} (see Figure 3a). Perform template matching over the entire image and perform non-maximum suppression to isolate the local peaks similar to the template 𝑇 of Lab 1 (see Figure 3b).

• maxima2grid()estimates 4 lattice grid points from each local maxima. The maxima coincides with the template center; based on the locations of {𝑎, 𝑏, 𝑐, 𝑑} on the original template, estimate the analogous grid points {𝑎′,𝑏′,𝑐′, 𝑑′} for each found maxima (see Figure 3c).

• refine_grid()Merge any “duplicate” grid points from neighbouring maxima, e.g. 𝑏′ with the 𝑐′ of a maxima to the left, and 𝑎′ with 𝑑′ of a neighbour below, by taking the mid-point between the two to recover a set of unique lattice points. Interpolate missing grid points e.g. based on weak maxima (see Figure 3d).

• grid2latticeunit()converts each found lattice grid point in image coordinates to the integer lattice grid shown in Figure 2a. For example, the points {𝑎, 𝑏, 𝑐} from the proposal corresponds respectively to {(0,0), (1, 0), (0,1)}. You can implement this any way you want, but clearly describe your intuition in the notebook. We show sample results in the notebook.

o Hint: Use the affine transformation to build the mapping. Consider multiple transformations to be applied locally in one region and then extend progressively to cover the entire image.

o Note that the lattice grid point location depends highly on the keypoint clusters. Grid points that coincide with any repeated patterns are all acceptable.

• draw_lattice()visualizes the grid points and their associated integer grids found by refine_grid() and grid2latticeunit()(see Figure 3e). This is provided for you.

Part 4: Exploratory Questions (30%)

• Patch-wise keypoint detection: Instead of detecting keypoints in a patch-wise manner, apply cv2.goodFeaturesToTrack to the entire image fence.jpg directly. Compare the difference when you take 𝑁 = (𝑃 ∙ 𝑄) ∙ 𝑁𝑝 points for the entire image vs. considering 𝑁𝑝 points for each (𝑃 ∙ 𝑄) patch. Briefly describe the difference in outcome and explain why differences arise. What are the benefits of patch-wise keypoint detection for translation symmetry detection?

• Clustering: Part 1 groups the points first with mean-shift clustering and then refines with a Kmeans clustering. For the first stage, explain the benefits of applying mean-shift instead of Kmeans. For the refinement stage, why do we discard the small clusters? Please briefly describe the relationship between the radius c and running time in the efficient implementation of mean-shift clustering.

• Affine transformation: In Part 2, affine transformation and RANSAC are used to find proposals. In the function of get_proposal(), only the points closest to 𝑎 are transformed. Why don’t we transform all points in the cluster to count the number of inliers?

• Different samples: Please apply your algorithm to at least 3 other images in the inputs folder. For each image, select two results you think are the best and append them to the notebook. In this question, you do not need to select the two results with the lowest A-score. Instead, you should notice that the A-score does not really give us the best results. Please briefly explain the disadvantages of A-score.

• Hard samples: Generate lattices for wallpaper.jpg and house.jpg and append your results to the notebook. Explain your outcome based on your method for generating the lattices. For those methods which succeed, explain which aspect of the lattice generating algorithm allows it to work on these samples. For those methods which fail, explain why your algorithm fails and possibilities for improvement. Possibilities for failure include not detecting the full lattice structure (some repetitive patterns are not detected), or a distorted structure mis-aligned to the underlying image.
