# Course project 2026

[Moodle project brief](https://learn.ucu.edu.ua/course/section.php?id=31282#section-10)

The final project contributes 25% to the total grade and is probably the most important activity in this course. The idea is that you will choose a topic that interests you the most, find the related literature, understand the approaches and their pros and cons, take one of the algorithms and then implement it numerically. You are supposed to write a report on the project, prepare and record the presentation and submit both for peer evaluation by the teachers and your classmates.

The course project is worth **25 of the 100 points**. This page is the project brief: what the project is, what you submit, the timeline, how it is assessed, and ideas for topics.

**In short**

- Any applied problem whose solution rests **essentially on linear algebra**: name the object, explain the algorithm, implement its core.
- Start from an application domain or from a type of method; **avoid LLM topics**.
- Teams of 2–3. Register your team and topic on Moodle by **Mon 19 October**.
- Questions: the course Slack channel, or at the start of any class.

## 1. The project

### What the project is

**The task.** Choose an applied problem you care about. Find the linear algebra inside it, learn the algorithms used to solve it, implement them, and test them honestly.

**Why it carries 25 points.** There is no final exam. The project is where you show the main skill of the course: _given an applied problem, identify the linear-algebraic structure, choose the factorization, predict its cost and failure modes, and implement it_.

**Format.** Teams of 2–3. Report, code and a recorded presentation, due mid-December; peer review in January.

### What your team will do

1. State the problem and why it matters in practice.
2. Formulate it in linear algebra: what is the matrix, what is unknown, which factorization or eigenproblem is involved.
3. Survey the available algorithms and choose **at most two**.
4. Explain the linear algebra behind them in your own words.
5. Predict their cost and their failure modes: conditioning, stability, scale.
6. Implement them; compare against a library routine and a benchmark.
7. Report what worked, what did not, and why.

### The one requirement: the LA test

The range of topics is deliberately broad. The only requirement is that the project rests **essentially** on linear-algebra concepts and algorithms. A topic passes if your report answers all three questions:

**The LA test**

1. **Object.** Which matrix, subspace, factorization or eigenproblem is at the centre of the problem?
2. **Algorithm.** Which linear-algebra algorithm solves it, and why does it work, at the level of this course?
3. **Your code.** Which part of it do you implement yourselves, rather than only call from a library?

The lecturer checks the LA test when approving your topic. Two examples:

- **Passes:** “Recommending films by low-rank matrix completion: alternating least squares versus singular value thresholding.” Object: a partially observed ratings matrix of low rank. Algorithms: two. Code: both.
- **Fails as stated:** “Predicting house prices with gradient boosting.” The data form a matrix, but no linear-algebra object is the subject of the project.
- **The same data, reframed to pass:** “Ridge regression through the SVD: how the singular values of the design matrix control the regularization path, and the cost of recomputing it for many penalties.”

### What you submit

- **Report:** 8–10 pages (PDF), excluding references, figures and appendices. Sections: problem; formulation; methods and cost; experiments; discussion.
- **Code:** repository or archive; the `README` says how to reproduce every figure and table.
- **Recorded presentation:** 10–12 minutes, **every team member speaks**, aimed at a classmate who has not read the report.
- **Contribution statement:** who did what, agreed by all members.
- **AI-use statement:** which tools, for what.

### Implementation: implement the core yourselves

- **Your own implementation.** Write the central algorithm from `numpy` building blocks: matrix products, triangular solves, norms. Python is the default; any language is fine.
- **A fair comparison.** Compare it with the library routine that does the same job (`scipy.linalg`, `sklearn`, `torch`, …) and, where one exists, with a published benchmark.
- **Honest failure is credited.** A method that fails, with a clear explanation of _why_ it fails, scores better than clean output with no understanding behind it.

### Experiments: what to measure

- **Accuracy:** residuals, errors against a known answer, or a standard benchmark metric.
- **Conditioning:** $\operatorname{cond}(A)$ of the matrices you actually factor, and its effect on accuracy.
- **Cost:** runtime against problem size, compared with the flop count you predicted.
- **Limits:** the size or condition number at which your method stops working.

**Example.** A least-squares project reports $\operatorname{cond}(A)$ for its design matrix, compares the errors of the normal equations, QR and `lstsq`, and plots runtime against $m$ next to the predicted $\sim 2mn^2$.

### Topics the course already covers

These are allowed only if you go **clearly beyond** the course version: a new application, a much larger scale, or a different algorithm compared with the course one.

| Lab | Topics |
| --- | --- |
| Lab 1 | fitting via QR; DFT/DCT energy compaction; the perceptron |
| Lab 2 | power iteration, Markov chains, PageRank; circulants and FFT |
| Lab 3 | covariance and whitening; Cholesky sampling; kernel ridge |
| Lab 4 | SVD compression and denoising; PCA and MDS; deblurring |
| Lab 5 | CG and preconditioning; randomized SVD; spectral clustering |

**Example.** “PageRank on a small graph” is Lab 2. “Personalized PageRank on the Wikipedia link graph: power iteration versus a Krylov solver” is a project.

### A warning about LLM topics

**Our advice: avoid topics about large language models**

LLMs are full of matrices, but they make poor linear-algebra projects:

- The linear algebra is buried: most of the effort goes into pipelines, GPUs, prompts and hyperparameters.
- You cannot implement the core yourselves or run controlled experiments on a laptop, so question 3 of the LA test fails.
- Results depend on compute and tuning more than on the method, so cost and failure modes cannot be isolated.
- The literature is mostly fast-moving preprints, which are hard to check.

**If you still want one:** it needs the lecturer’s explicit approval at registration, one clearly isolated linear-algebra object, and experiments that run on a laptop.

## 2. Timeline and assessment

### Timeline

| Date | Milestone |
| --- | --- |
| Mon 19 Oct | **Team and topic registration** on Moodle |
| Thu 22 Oct | Topic approved, or returned with a suggested reframing |
| Mon 2 Nov | **Interim report 1**: scoping memo |
| Mon 16 Nov | **Interim report 2**: working baseline |
| Mon 14 Dec | **Final submission**: report, code, recording, statements |
| 11–24 Jan | **Peer review** in Moodle Workshop |
| by 29 Jan | Staff grades; short online Q&A where needed |

All deadlines are 23:59 Kyiv time.

- Each interim report gets written feedback within a week.
- Lab 5 is due at the end of November; the three weeks after it are the main project window.

### What each milestone contains

**Registration (one paragraph).** Team members; the application domain and the method family; the problem; the data or benchmark; the **linear-algebra object**; one or two candidate algorithms; two or three references.

**Interim report 1: scoping memo, 2 pages.**

- the problem, the aim and the precise task;
- the linear-algebra formulation;
- possible approaches, their pros and cons, and their **predicted cost**;
- the chosen method(s), the plan, and who does what;
- 3–5 references you have actually read.

**Interim report 2: working baseline, 2 pages plus a link to the code.**

- a first implementation running on small data;
- a first comparison with a library routine, with one figure;
- the outline of the final report;
- what is not working yet, and any change of plan.

Why this milestone: a project whose code first runs in December has no time left to learn from its experiments. Interim report 2 moves that moment to November.

### Grading: 25 points

| Points | Component | How it is marked |
| --- | --- | --- |
| 2 | Interim report 1 | 2 complete, passes the LA test; 1 needs revision; 0 missing |
| 3 | Interim report 2 | 3 baseline runs, with results; 2 partial; 1 plan only; 0 missing |
| 12 | Staff grade | report, code, presentation; by the criteria below |
| 4 | Peer grade | classmates’ marks for your report and presentation, by the same criteria |
| 4 | Review quality | the marks and comments _you_ give |
| **25** |  |  |

### Assessment criteria

Staff and peers use the **same five criteria**, each scored 0–3. A score of 0 means missing, or not recognisable as an attempt.

| Criterion | Weight | 3 | 2 | 1 |
| --- | --- | --- | --- | --- |
| **A.** Problem and formulation | 2 | problem and its practical value clear; matrix, unknowns and factorization stated precisely; method choice justified by the structure | formulation correct, but the link from structure to method choice is left implicit | LA appears only in passing, or the formulation is vague or wrong |
| **B.** Mathematics of the method | 3 | key ideas explained correctly in the team’s own words; central claims proved or convincingly sketched; notation consistent; sources cited | correct but closely follows the sources, or has gaps in the key step | errors in the key step, or a paraphrase of sources without understanding |
| **C.** Cost and failure modes | 2 | flop count and memory predicted and checked; conditioning and stability discussed for the actual matrices; limits of the method found experimentally | cost stated but not checked, or conditioning mentioned without evidence | cost or limitations mentioned only in general terms |
| **D.** Implementation and experiments | 3 | core algorithm implemented by the team; fair comparison with a library routine and a benchmark on accuracy and runtime; every figure reproducible from the `README` | implementation works, but the comparison is thin or not fully reproducible | library calls only, or results that cannot be reproduced |
| **E.** Communication | 2 | report readable by a classmate; figures labelled and honest; presentation within time, every member speaks, the main result is clear | mostly clear, with lapses in structure, figures or timing | hard to follow; key results buried or missing |

- Staff grade $= \frac{1}{3}(2A + 3B + 2C + 3D + 2E)$, out of 12.
- Peer grade: the same weighted score from each reviewer, averaged and rescaled to 4.

### Peer review

- It runs in **Moodle Workshop**, the tool used in the workshop tutorials 2.2, 3.2 and 6.2.
- Each student, individually, reviews two reports, with their recordings, from other teams.
- For each criterion you give a score 0–3 and at least two sentences of justification, then one paragraph of advice.

**Your review quality (4 points):**

- 2 from Workshop: how close your scores are to the other reviewers’ scores;
- 2 from staff: are your comments specific, correct and useful to the authors?

**Safeguards:** staff moderate the peer grade and override clear outliers. A review not submitted scores 0 for that review.

### Teams, individual grades, lateness

- **Teams.** Registration is first come, first served. Two teams may share a topic area only with clearly different problems or methods.
- **Individual grades.** All members receive the team’s grade by default. Staff may adjust an individual grade when the contribution statement, the presentation or a Q&A shows a clearly unequal contribution.
- **Late submissions.** Interim reports: the course late policy applies; feedback is still given. Final submission: a report that misses the Workshop submission phase cannot be peer-reviewed, so its peer grade is 0.

### AI tools

- **Allowed:** help with code, language editing, and finding literature.
- **Required:** declare the use in the AI-use statement.
- **Required:** every member can explain every equation and every line of the core code.
- **Required:** references are real and have been read. An invented reference is treated as a serious breach.

## 3. Topic ideas

### Choosing a topic: two ways in

- **Route 1: start from an application domain.** Audio and speech; image processing; vision-assisted navigation; recommender systems; physical phenomena (vibrations, diffusion, fluid flow, climate). Which linear-algebra problems does the domain keep solving?
- **Route 2: start from a type of method.** Wavelet and other fast transforms; a factorization (QR, Cholesky, SVD, NMF, tensor); randomized linear algebra; iterative and Krylov solvers; spectral methods on graphs. Where does the method do real work?

Either way, a topic is **a domain plus a method**, with data you can obtain. Your work or your thesis is a good source of either. Then apply the LA test.

| Domain | Methods | Example topic |
| --- | --- | --- |
| Audio | short-time Fourier transform, wavelets, NMF | separating instruments in a recording by NMF of its spectrogram |
| Image processing | wavelets, SVD, sparse solvers | image compression with wavelets versus the DCT |
| Vision-assisted navigation | homogeneous least squares, SVD, sparse least squares | visual odometry: camera motion from the essential matrix |
| Recommender systems | low-rank completion, randomized SVD | alternating least squares versus singular value thresholding |
| Physical phenomena | eigenproblems, sparse solvers, SVD | dynamic mode decomposition of fluid-flow or traffic data |

The ideas below are grouped by the five themes of the course, with the linear-algebra core of each in brackets. They are **examples, not a menu**.

### Ideas: fitting, estimation, inverse problems

- **Kalman filtering as recursive least squares**, and its more stable square-root form _[QR updates, Givens rotations]_
- **Positioning from noisy distances**: GPS, Wi-Fi or UWB indoor positioning _[nonlinear least squares, Gauss–Newton]_
- **Instrumental variables and two-stage least squares**; “controlling for” as projecting out _[projections]_
- **Total least squares** when the inputs are noisy too _[SVD]_
- **Tomography**: Kaczmarz’s method versus CGLS _[row projections, Krylov methods]_
- **Optimal experimental design and sensor placement** _[log det, Cholesky, A- and D-optimality]_
- **Ranking from pairwise results**: Massey and Colley ratings for sports _[least squares on graphs]_

### Ideas: spectra, Markov chains, graphs

- **Ranking beyond Lab 2**: HITS, personalized PageRank on a large real graph _[eigenvectors, Krylov solvers]_
- **Community detection on a real network**: normalized cuts, modularity _[Laplacian eigenvectors, Lanczos]_
- **Graph signal processing**: the graph Fourier transform and denoising on graphs _[Laplacian eigenbasis]_
- **Manifold learning**: Laplacian eigenmaps, diffusion maps _[sparse symmetric eigenproblems]_
- **How fast does a Markov chain mix?** Card shuffling, MCMC convergence _[spectral gap]_
- **The QR algorithm for eigenvalues**: Hessenberg reduction, shifts, deflation _[Householder, QR]_
- **Optimal transport by the Sinkhorn algorithm** _[matrix scaling, positive matrices]_

### Ideas: symmetric and positive definite matrices

- **Gaussian process regression** and how to scale it _[Cholesky, log det, low-rank approximations]_
- **Kernel methods for large data**: Nyström approximation versus random Fourier features _[low-rank PSD matrices]_
- **Covariance estimation in high dimension**: shrinkage (Ledoit–Wolf), the nearest correlation matrix _[PSD cone, eigenvalues]_
- **Portfolio optimization and factor models of risk** _[quadratic forms, Cholesky, low rank plus diagonal]_
- **Gaussian graphical models**: what zeros in the precision matrix mean _[inverse covariance, Schur complements]_
- **Diffusion models**: the forward noising process in closed form _[Gaussian vectors, covariance]_
- **Second-order optimization**: Gauss–Newton and natural gradient _[Hessians, Fisher information, CG]_

### Ideas: low-rank structure

- **Recommender systems**: alternating least squares versus singular value thresholding _[low-rank completion]_
- **Topic modelling**: NMF versus latent semantic analysis _[NMF, truncated SVD]_
- **Word embeddings from co-occurrence counts**: PPMI plus SVD versus word2vec _[SVD]_
- **Compressing a small image classifier** by low-rank approximation of its layers _[SVD, Eckart–Young]_
- **Robust PCA**: video background subtraction _[low rank plus sparse]_
- **Tensor decompositions**: CP, Tucker, HOSVD _[multilinear SVD]_
- **Hidden factors**: ICA, CCA, probabilistic PCA, factor analysis _[generalized eigenproblems]_
- **Structure from motion**: the Tomasi–Kanade factorization on real video _[rank-3 SVD]_

### Ideas: scale, sparsity, randomization

- **Randomized least squares**: sketch-and-precondition (Blendenpik, LSRN) versus QR _[random projections, QR]_
- **Vector databases**: random projections and the Johnson–Lindenstrauss lemma, product quantization _[random matrices, nearest neighbours]_
- **Image editing and deblurring with preconditioned CG** _[sparse SPD systems, Krylov methods]_
- **SLAM and bundle adjustment**: why sparsity and the Schur complement make them feasible _[sparse least squares]_
- **Sparse direct solvers**: fill-in and reordering (minimum degree, nested dissection) _[LU, Cholesky, graphs]_
- **Mixed precision**: solving in half precision, refining in double _[LU, conditioning, iterative refinement]_
- **Matrix-free deep learning**: Hessian-vector products and Lanczos for the loss-surface spectrum _[Krylov methods]_

### Ideas: signals, audio, images, vision

- **Wavelets and image compression** (JPEG 2000) _[orthogonal transforms, fast algorithms]_
- **Audio source separation**: NMF of spectrograms _[NMF, short-time Fourier transform]_
- **Compressed sensing**: recovering sparse signals with orthogonal matching pursuit _[projections, coherence]_
- **Visual odometry for navigation**: the eight-point algorithm and the essential matrix _[SVD, homogeneous least squares]_
- **Speaker or face verification** with subspace methods _[PCA, LDA, generalized eigenproblems]_
- **Edge detection and image filtering** as linear operators _[convolution, Toeplitz and circulant matrices]_
- **Frequency estimation in radio signals**: MUSIC and ESPRIT _[subspaces, eigenvectors of covariance matrices]_

### Ideas: real-world physical phenomena

- **Dynamic mode decomposition** of fluid-flow, traffic or epidemic data _[SVD, eigenvalues]_
- **Vibration modes of a bridge or a building** _[generalized symmetric eigenproblem]_
- **Heat diffusion and the Poisson equation on a grid** _[sparse SPD systems, CG, FFT]_
- **Climate patterns**: empirical orthogonal functions, the PCA of space-time fields _[SVD]_
- **Weather data assimilation**: the ensemble Kalman filter _[low-rank covariance, least squares]_
- **Electrical networks and Kirchhoff’s laws** _[graph Laplacian, least squares]_

### Topics from past years

- Discrete wavelet transform
- Edge detection algorithms
- Matrix factorization for topic modelling
- Military object tracking
- PageRank for image search
- Propaganda classification
- Speaker verification techniques
- UAV detection through RF analysis
- SVD applications in bioinformatics
- Investigation of the SURF algorithm
- Applications of spectral graph theory
- Frequency transforms for image recognition and inpainting
- Estimation of signal parameters
- Face recognition with NMF

These titles name the application only; a 2026 title names the linear algebra too. For example: “Detecting drones from radio spectra: subspace methods (MUSIC, ESPRIT) for frequency estimation”.

### Where to start reading

- G. Strang, _Linear Algebra and Learning from Data_, Wellesley–Cambridge Press, 2019.
- L. N. Trefethen, D. Bau, _Numerical Linear Algebra_, SIAM, 1997.
- G. H. Golub, C. F. Van Loan, _Matrix Computations_, 4th ed., Johns Hopkins, 2013.
- S. L. Brunton, J. N. Kutz, _Data-Driven Science and Engineering_, 2nd ed., Cambridge, 2022.
- P.-G. Martinsson, J. A. Tropp, Randomized numerical linear algebra: foundations and algorithms, _Acta Numerica_ 29, 2020.

Survey papers and the documentation of the library you compare against (`scipy`, `sklearn`, …) are often the fastest way into a topic.

## Project checkpoint 0: team and topic registration

[Moodle registration instructions](https://learn.ucu.edu.ua/course/section.php?id=31282#section-9)

Form a team of 2–3 students and register your project topic. **One member submits on behalf of the team** in this **[spreadsheet](https://docs.google.com/spreadsheets/d/1c0TW22wxlN4tR_YO1496FqyZXTyjLSAxlVg9ogPaUfw/edit?usp=sharing).**

**Deadline:** Mon 19 October, 23:59 Kyiv time.

This checkpoint is not graded, but no later project work is accepted without an approved topic.

Please provide:

1. Working title, naming both the application and the linear algebra
2. Team members (full names, UCU emails) and a contact person
3. Application domain (choose from the list)
4. Method family (choose from the list)
5. The problem, in 2–4 sentences: input, output, why it matters
6. Data or benchmark: name, link, size, and confirmation that you can access it
7. Linear-algebra formulation: the central linear-algebra object and what you need to do with it. The object may be a matrix or a linear operator (it need not be stored as a matrix), a basis or change of basis, a subspace, a geometric transformation, a quadratic form, a linear dynamical system, or a tensor. State its size and the structure your method relies on: sparsity, symmetry, orthogonality, low rank, a special pattern (Toeplitz, circulant), or a different number system (finite fields, integer lattices). Then say what the task is: to solve, factor, approximate, change basis, project, find eigenvalues or singular values, or analyse stability.
8. One or two candidate algorithms, and which part you will implement yourselves
9. Relation to the course: does it overlap a lab topic (how do you go beyond it)? Is it LLM-related (if so, why does it still pass the LA test)?
10. Two or three references (full citation plus link, at least one textbook or survey)
11. A one-line backup topic, in case of a clash

## Templates

- [Final project files on Moodle](https://learn.ucu.edu.ua/mod/folder/view.php?id=77318)
- [Local template and examples](examples/)

## Assignment pages

- [First interim report](first-interim-report.md) (9 November 2026, 23:59)
- [Second interim report](second-interim-report.md) (16 November 2026, 23:59)
- [Final report submission](final-report-submission.md) (14 December 2026, 23:59)
- [Peer evaluation of the LA projects](peer-evaluation.md) (11 January 2027, 23:59)
- [Evaluation of the peer review quality](evaluation-of-the-peer-review.md) (30 January 2027, 00:00)
