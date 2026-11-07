# First interim report

[Moodle assignment](https://learn.ucu.edu.ua/mod/assign/view.php?id=77320)

**Deadline:** 9 November 2026, 23:59 Kyiv time.

## Interim report 1: scoping memo

**Worth:** 2 points.

**Submission:** one PDF per team, uploaded by the contact person.

**Format:** the project report template with `\stage` set to 1. At most 2 pages, project card included; references are not counted.

The memo shows that your project is well defined and feasible before you start coding. It must contain:

1. **Project card**, updated from your registration, including any reframing we agreed.
2. **Problem and aim:** what goes in, what comes out, and why it matters. Then the **precise task**: what result will count as success. For example, “predict held-out ratings with RMSE below that of the baseline”, or “reconstruct the image to relative error 10⁻³”.
3. **Linear-algebra formulation:** the central linear-algebra object and what you need to do with it. The object may be a matrix or a linear operator (it need not be stored as a matrix), a basis or change of basis, a subspace, a geometric transformation, a quadratic form, a linear dynamical system, or a tensor. State its size and the structure your method relies on: sparsity, symmetry, orthogonality, low rank, a special pattern (Toeplitz, circulant), or a different number system (finite fields, integer lattices). Then say what the task is: to solve, factor, approximate, change basis, project, find eigenvalues or singular values, or analyse stability.
4. **Possible approaches:** two or three from the literature, with pros and cons, **predicted cost** as a formula in the problem size (for example, ~2mn² flops for the Householder QR of an m×n matrix) plus memory, and what is likely to go wrong (conditioning, slow convergence, scale).
5. **Chosen method(s) and plan:** which one or two you will pursue and why, what you will implement yourselves, the steps up to interim report 2 (23 Nov) and the final report (14 Dec), and who does what.
6. **References:** 3–5 sources you have actually read, each cited in the text, with a full citation and a link or DOI.

Use the guidance boxes in the template; delete them (or set `\showguidefalse`) before you submit.

## Grading (2 points)

- **2**: all six items are present; the topic passes the LA test (a clear linear-algebra object, an algorithm you can explain, and a part you implement yourselves); the changes requested in our registration comments are made.
- **1**: items are missing, or the linear-algebra object or the success criterion is unclear, or the requested changes are only partly made.
- **0**: not submitted.

We return written feedback within a week. The course late policy applies; late memos still receive feedback.
