# Decisions before submitting interim report 1

The review fixes correct the mathematics and restore the planned library baseline.
They do not make this draft ready to submit: the choices below still need agreement.
Recommendations are proposals, not decisions already made by the team.

## 1. Who owns each part?

The assignment asks who does what. A list of tasks without names does not answer it.
Choose a lead for data/calibration, features and matching, synthetic data and metrics,
eight-point estimation, RANSAC, experiments, and writing. One person can lead several
parts; everyone can help and should understand the core algorithm.

**Needed answer:** a name beside each work package. Provisional assignments are fine.

## 2. What are the actual deadlines?

The draft says 30 November for interim 2 and 21 December for the final report.
The local final-submission instructions say 14 December. Local interim instructions
conflict: the first-interim brief mentions 23 November, while the second-interim page
says 16 November. These files may not include later announcements.

**Needed answer:** confirm the latest Moodle or teacher announcement, including any
extension. Then work backwards from those dates. The PR preserves the draft dates
because it cannot establish that an extension was or was not granted.

## 3. What exactly does the synthetic accuracy target mean?

The draft promises rotation error below 1 degree and translation-direction error
below 5 degrees with “1 pixel noise.” That is not yet a repeatable test. A scene with
many well-spread points and clear camera movement is easier than a scene with few
points and almost no movement.

Agree on the number of points, camera calibration/image size, scene depth, camera
motion, number of trials, and whether there are incorrect matches. Also specify the
noise distribution and where it is added. For example, independent Gaussian noise
with a standard deviation of 1 pixel in each image coordinate is one possible choice.

Decide whether the limits apply to the median, a high percentile, or every trial.
A median describes a typical result; a 90th percentile also exposes many bad cases.
Neither means every trial succeeds.

**Recommendation:** use a fixed, reproducible nondegenerate setup for the headline
target, report median and 90th-percentile errors across multiple seeded trials, and
test planar scenes/small movement separately as stress tests. Agree numerical settings
before interpreting results. Report failures rather than silently excluding them.

## 4. What counts as a RANSAC inlier?

RANSAC proposes a camera-motion model and asks which point matches agree with it.
It needs a distance measure and a cutoff. A loose cutoff accepts wrong matches;
a tight cutoff rejects useful noisy matches. The raw epipolar expression changes
when the same matrix is multiplied by a constant, although its geometry is unchanged.

**Recommendation:** use Sampson error, an approximation to the geometric correction
needed to make a match fit. Choose a threshold based on expected image noise, state
whether the error is squared, and state the coordinate units. Pixel coordinates and
calibrated coordinates have different scales, so the same numerical cutoff cannot
simply be copied between them.

**Needed answer:** residual definition, units and threshold rule. Use a consistent
evaluation protocol when comparing the custom estimator and the library baseline.

## 5. Are we estimating motion between frames or a whole path?

Two images reveal translation direction but not distance travelled. Suppose a drone
moves 1 metre in one step and 3 metres in the next. Giving both estimated directions
length 1 loses that difference. Multiplying the final path by one constant cannot
repair it.

**Recommendation:** make rotation and translation direction for each frame pair the
main deliverable. If a path is shown using equal-length steps, label it illustrative.
A meaningful path requires an additional method to connect translation scales
between steps, which adds work. Using ground-truth distances for a visualization
must also be disclosed and is not independent trajectory recovery.

**Needed answer:** pairwise estimates only, pairwise estimates plus an illustrative
path, or extra work on relative scale. The PR leaves the existing trajectory promise
for the team to resolve.

## 6. What will the singular values tell us?

The estimator seeks a direction that makes A times that direction nearly zero.
For perfect, nondegenerate data with at least nine matches, one singular value is
zero by design. The ordinary condition number is then infinite even when the answer
is well determined. An infinite value alone does not mean the method failed.

Two separate questions matter: are coordinate scales badly balanced, and is the
best solution direction clearly separated from other possible directions?
The ratio of the largest to the eighth singular value can help describe the nonzero
spectrum. The separation of the eighth and ninth values helps investigate ambiguity.
Exact degeneracy needs special handling because both can be zero.

**Recommendation:** plot spectral diagnostics beside actual pose errors first, then
assess whether they predict failures. Do not invent a universal cutoff in advance.
Compare like-for-like coordinate systems and document normalization.

**Needed answer:** which quantities to plot and whether the first implementation only
reports warnings or also rejects frame pairs. If pairs are rejected, report how many
so accuracy does not improve merely by hiding difficult cases.

## Scope already restored

The OpenCV five-point baseline and planar/small-baseline experiments come from the
existing project plan. No new approval is needed to include them. If the team has
intentionally dropped them, discuss and document that scope change explicitly.

## Sources and AI use

- [First-interim requirements](../docs/ucu/first-interim-report.md)
- [Second-interim instructions](../docs/ucu/second-interim-report.md)
- [Final-submission instructions](../docs/ucu/final-report-submission.md)
- [Approved project scope and professor's feedback](../docs/our-case.md)

Codex assisted with the review, immediate corrections, and this decision guide.
The report includes a short AI-use statement. The team remains responsible for
checking the text and understanding the mathematics.
