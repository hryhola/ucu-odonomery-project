# Visual odometry for drone navigation

| Registration | Details |
| --- | --- |
| Entry | No. 2, submitted 17 October 2026 |
| Status | Approved |
| Team | Bohdan Prokhorov, Markiian Yatsyshyn, Vladyslav Hryhola |
| Contact | Bohdan Prokhorov |
| Application domain | Computer vision and navigation |
| Method family | SVD and low-rank approximation |

## Problem

- **Input** — A sequence of camera frames with feature points matched between consecutive frames and known camera calibration.
- **Output** — Relative rotation and translation direction at each step, chained into a camera trajectory.
- **Motivation** — Camera-based motion estimation helps robots, drones, and vehicles navigate where GPS is unavailable or unreliable.

## Data

The [UZH-FPV Drone Racing Dataset](https://fpv.ifi.uzh.ch/) contains 31 indoor and outdoor flight sequences from a racing quadrotor flown by an expert pilot. It includes camera images, IMU measurements, and event-camera data. Laser-tracked ground truth is public for 16 sequences.

## Linear-algebra formulation

Build an $N \times 9$ matrix $A$ from $N \ge 8$ point matches between two frames. Estimate the essential matrix $E$ by solving the homogeneous least-squares problem $\min_{\lVert e\rVert_2=1} \lVert Ae\rVert_2$ using the right singular vector corresponding to the smallest singular value. Project $E$ to rank two with singular values $(s, s, 0)$ by SVD and decompose it into $R$ and $t$.

Without point normalisation, $A$ can be poorly conditioned. Translation is known up to scale.

## Planned methods and experiments

1. Implement the eight-point algorithm with and without Hartley normalisation. Build $A$, solve the homogeneous least-squares problem, project onto the essential-matrix set, and decompose $E$ into $R$ and $t$ using a library SVD.
2. Implement RANSAC around the same estimator. Use OpenCV for feature matching and as a five-point baseline. Compare an Easy and a Hard sequence.

## Professor's feedback

Rostyslav Hryniv approved the topic and suggested the following checks.

- [ ] **Pose ambiguity.** Resolve the four-fold ambiguity when decomposing $E$ by triangulating matched points. Formulate triangulation as a homogeneous least-squares problem and solve it by SVD.
- [ ] **Degenerate cases.** Test small camera baselines and points on a single plane. Check whether the gap between the two smallest singular values of $A$ flags these cases.
- [ ] **Evaluation with unknown scale.** Start with synthetic data with known relative poses. Measure rotation error and translation-direction error for each frame pair.
- [ ] **UZH-FPV camera model.** Check the calibration and undistort the images or feature coordinates if the camera uses a fisheye model.
- [ ] **Easier real sequence.** Consider KITTI or EuRoC for the easier sequence. UZH-FPV racing footage may be difficult because of the high speeds.
- [ ] **Hartley normalisation.** Estimate the fundamental matrix $F$ from pixel coordinates and compare $\operatorname{cond}(A)$ with and without normalisation. The effect on conditioning is expected to be largest in pixel coordinates.

## Relation to the course

Lab 1 solves the inhomogeneous problem $Ax = b$ by QR. Our problem is homogeneous ($Ae = 0$ with $\lVert e\rVert_2 = 1$ in the exact case) and uses the SVD. Lab 4 uses the SVD for compression and PCA. Here it finds a null direction and projects onto a constrained set of matrices.

**LLM relation** — None.

## References

- R. Hartley, “In defense of the eight-point algorithm,” *IEEE TPAMI* 19(6), 1997.
- R. Hartley and A. Zisserman, *Multiple View Geometry in Computer Vision*, 2nd ed., Cambridge University Press, 2004. Chapters 9 and 11 cover epipolar geometry, the essential matrix, and the eight-point algorithm. Chapter 4 covers normalisation and RANSAC. Appendix A5 covers homogeneous least squares by SVD.
- J. Delmerico et al., “Are We Ready for Autonomous Drone Racing? The UZH-FPV Drone Racing Dataset,” ICRA 2019. [Paper](http://rpg.ifi.uzh.ch/docs/ICRA19_Delmerico.pdf)

## Backup topic

Structure from motion on the same dataset.
