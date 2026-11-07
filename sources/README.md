# Sources

Focused reading set for the team's eight-point/SVD visual odometry project. See the [project brief](../docs/our-case.md) and [source review](../docs/source-review.md) for the scope and audit findings.

## Three core sources

1. **R. Hartley, “In defense of the eight-point algorithm,” IEEE TPAMI 19(6), 580–593, 1997.** [DOI](https://doi.org/10.1109/34.601246) · [Author PDF](https://users.cecs.anu.edu.au/~hartley/Papers/fundamental/fundamental.pdf)
   - Local PDF: `In Defence of the 8-Point Algorithm (Richard I. Hartley).pdf`.
   - Read for the eight-point algorithm, coordinate normalisation, and conditioning. The local 28-page author version is complete; its pagination differs from the journal version.
2. **R. Hartley and A. Zisserman, Multiple View Geometry in Computer Vision, 2nd edition, Cambridge University Press, 2004.** [Authors' page and errata](https://www.robots.ox.ac.uk/~vgg/hzbook/)
   - Local PDF: `Multiple View Geometry in Computer Vision, 2nd Edition (Richard Hartley, Andrew Zisserman).pdf`.
   - Main mathematical reference. Read §9.6 for E and pose ambiguity; §11.1–11.2 for eight-point estimation; §4.4 and §4.7 for normalisation and RANSAC; §11.9 for degeneracies; §12.2 for linear triangulation; A5.3 for homogeneous least squares. The local 673-page PDF contains the full book structure, including appendices and index.
3. **J. Delmerico et al., “Are We Ready for Autonomous Drone Racing? The UZH-FPV Drone Racing Dataset,” ICRA, 2019.** [Official PDF](https://rpg.ifi.uzh.ch/docs/ICRA19_Delmerico.pdf) · [Dataset](https://fpv.ifi.uzh.ch/)
   - Local PDF: `Are We Ready for Autonomous Drone Racing, The UZH-FPV Drone Racing Dataset (Jeffrey Delmerico, Titus Cieslewski, Henri Rebecq, Matthias Faessler, Davide Scaramuzza).pdf`.
   - Read for the sensors, flight conditions, and dataset difficulty. The complete 7-page local PDF matches the official file. Use current dataset documentation alongside the paper because ground truth and the sequence catalogue have changed since publication.

## Best supplementary PDF

**J. W. Demmel, Applied Numerical Linear Algebra, SIAM, 1997.**

- Local PDF: `Applied Numerical Linear Algebra (James W. Demmel).pdf`.
- Read §3.2.3 for SVD, §3.3 for perturbation theory, and §3.5 for rank-deficient least squares; consult chapter 5 when deeper SVD analysis is needed.
- This is the most useful existing supplementary book for explaining conditioning, stability, and numerical failure modes. It complements the geometry sources without expanding the project into machine learning or control.

## Essential online supplements

- [OpenCV camera calibration and 3D reconstruction](https://docs.opencv.org/4.x/d9/d0c/group__calib3d.html): `findEssentialMat`, `recoverPose`, `findFundamentalMat`, and the linked fisheye documentation. Record the actual library version and estimator settings in experiments.
- [UZH-FPV dataset files and calibration](https://fpv.ifi.uzh.ch/datasets/) and [companion repository](https://github.com/uzh-rpg/uzh_fpv_open): select public ground truth, the correct sensor calibration, timestamps, and coordinate transforms. Follow the dataset site's citation guidance for the ground-truth method used.
- **D. Nistér, “An Efficient Solution to the Five-Point Relative Pose Problem,” IEEE TPAMI 26(6), 756–770, 2004.** [DOI](https://doi.org/10.1109/TPAMI.2004.17). Targeted background for the five-point baseline; no local PDF is included in this collection.
- [EuRoC MAV dataset](https://projects.asl.ethz.ch/datasets/euroc-mav/): consult and cite its publication only if it is selected for the easier real-data experiment.

## Optional background and archive

For basic LA explanations, consult **Lay et al., Linear Algebra and Its Applications, 6th edition**, chapter 6 and §7.4, as needed. Strang's *Introduction to Linear Algebra* is an alternative. Neither is required in the focused PDF bundle. The other general LA books remain available locally but are not part of the project's default reading set.

`odometry-selected-sources.zip` contains this README and the **four PDFs** listed in the core and supplementary PDF sections. Online-only references and optional background books are not included. Links to `../docs/` refer to the project checkout and will not resolve in the standalone archive.

PDFs and the ZIP are local reading materials excluded from Git. Do not publish the archive or redistribute copyrighted books without permission.
