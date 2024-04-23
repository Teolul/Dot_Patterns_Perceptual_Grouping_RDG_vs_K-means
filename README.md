# Dot Patterns Perceptual Grouping: RDG vs K-means

University project about the principles and models of human perception, addressing the human perception of Dot Patterns through the Gestalt laws and their algorithmic reproduction.\
Furthermore, an implementation of G. Papari and N. Petkov's algorithm is proposed. This is used to compute and show a Reduced Delaunay Graph that approximates how a human perceives Dot Patterns. The implementation is based on Papari and Petkov's paper "Algorithm That Mimics Human Perceptual Grouping of Dot Patterns" for the Institute of Mathematics and Computing Science in the University of Groningen.\
A summarized explanation of the algorithm, among other things, can be found in the presentation file in this repository.\
Link to the paper: https://www.cs.rug.nl/~petkov/publications/2005LNCS3704_grouping_dots.pdf

Link to the Google Slides presentation in Italian: https://docs.google.com/presentation/d/1gU4DdQmeBwjRghgNckoXqe1z2C823ul-mzq3W7HbTIo/edit?usp=sharing

Link to the Google Slides presentation in English: https://docs.google.com/presentation/d/1yELGL9EbTdOBSm8ia-DKzZKWTdArHPNjfCTun1iTgjc/edit?usp=sharing

![Image 1](https://github.com/Teolul/Dot_Patterns_Perceptual_Grouping_RDG_vs_K-means/blob/main/faces.PNG "Image showing a dotted face, a dotted face connected with a Reduced Delaunay Graph and a dotted face clustered with the K-Means algorithm side by side.")

## Libraries used:

numpy

scipy

matplotlib

sklearn

## Documentation:

In notebook.ipynb execute all the code snippets from the beginning.

The following paragraphs explain the various functions in the notebook. To avoid repetition, here are explained the most common parameters that can be found:

- num_points (int): the number of points considered for generating a dataset.
- noise_factor (float): how much the points are scattered in generating a dataset.
- points (numpy.ndarray): the points considered for plotting a dataset.

`generate_face(num_points, noise_factor=0.01):`

- Computes a point dataset in the shape of a face with two eyes and a mouth.
- Parameters:
  - num_points: see above.
  - noise_factor: see above.

`generate_spiral(num_points, xtranslation=0, ytranslation=0, turns=2, scale= 0.08, noise_factor=0.01):`

- Computes a point dataset in the shape of a spiral.
- Parameters:
  - num_points: see above.
  - xtranslation (float): the translation of the spiral on the horizontal axis.
  - ytranslation (float): the translation of the spiral on the vertical axis.
  - turns (int): the number of turns in the spirals. The larger this parameter is, the longer and complex the spiral is.
  - scale (float): the size at which the spiral is computed.
  - noise_factor: see above.

`merge_spirals(spiralA, spiralB, degrees=0):`

- Computes a point dataset in the shape of a double spiral.
- Parameters:
  - spiralA (numpy.ndarray): the first spiral considered for the output.
  - spiralB (numpy.ndarray): the second spiral considered for the output.
  - degrees (float): how much the second spiral will be rotated.

`generate_doughnut(outer_radius, num_outer_points, outer_noise_level, inner_radius, num_inner_points, inner_noise_level):`

- Computes a point dataset in the shape of two concentric circles.
- Parameters:
  - outer_radius (float): the radius of the outer circle.
  - num_outer_points (int): the number of points in the outer circle.
  - outer_noise_level (float): how much the points in the outer circle are scattered.
  - inner_radius (float): the radius of the inner circle.
  - num_inner_points (int): the number of points in the inner circle.
  - inner_noise_level (float): how much the points in the inner circle are scattered.

`generate_barred_spiral(num_points, radius, noise_factor, xTranslation, yTranslation):`

- Computes a point dataset in the shape of two intertwined semi-circles.
- Parameters:
  - num_points: see above.
  - radius (float): the radius of both semi-circles.
  - noise_factor: see above.
  - xtranslation (float): the translation of the lower semi-circle on the horizontal axis.
  - ytranslation (float): the translation of the lower semi-circle on the vertical axis.

`mix_fixed_points():`

- Computes a point dataset in the shape of a few squares scattered in fixed positions on the plane.

`plot_points(points):`

- Shows a scatter plot from the point dataset passed as parameter.
- Parameters:
  - points: see above.

`delaunay_triangulation(points):`

- Shows a Delaunay Triangulation plot from the point dataset passed as parameter.
- Parameters:
  - points: see above.

`rdg_compute(points, threshold=2.5):`

- Computes a Reduced Delaunay Graph from the point dataset passed as parameter using Papari and Petkov's algorithm.
- Parameters:
  - points: see above.
  - threshold (float or string):
    - if it's a positive number, it's used as a static threshold for the values in the map.
    - if it's "mean", a dynamic threshold is computed based on the mean of the values in the edge map.
    - if it's "area", a dynamic threshold is computed based on the area of the smallest enclosing circle of all the points.

`kmeans_clustering(points, n_clusters):`

- Computes k-means clustering on the point dataset passed as parameter.
- Parameters:
  - points: see above.
  - n_clusters (int): the number of clusters to detect for the k-means algorithm.

`compute_rdg_vs_kmeans(data_set, threshold, num_cluster, title="Data set"):`

- Computes and plots the point dataset, its delaunay graph, its rdg and its k-means clustering.
- Parameters:
  - data_set (numpy.ndarray): the considered point dataset.
  - threshold (float): the threshold for the rdg_compute.
  - num_cluster (int): the number of clusters to detect for the k-means algorithm.
  - title (string): the title put at the top of the point dataset plot.

Further explanations of what the various functions do can be found in the comments inside the notebook.\
The various point datasets can be generated by executing the function and the corresponding snippet with the function call.\
Then, the generated datasets can be used as parameters for the four plotting functions (plot_points, delaunay_triangulation, rdg_compute, kmeans_clustering). Tweaking the thresholds and other parameters is recommended to achieve better results.\
Other point datasets in the form of a numpy array can be used to see other results.
