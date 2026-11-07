# Visual odometry for drone navigation

This UCU Linear Algebra team project estimates relative rotation and translation direction from matched points in calibrated camera frames. Translation scale is unknown.

The team develops the implementation and is responsible for explaining its mathematics and core code. AI assistance focuses on explaining concepts, answering questions, and giving feedback on the team's reasoning and code. The team records AI use in the report.

- The [project brief and professor's checklist](docs/our-case.md) describe the approved scope and planned experiments. The [course materials](docs/ucu/OVERVIEW.md) contain the requirements and report templates.
- [implementation/](implementation/) is for the team's eight-point estimator, Hartley normalisation, and RANSAC. The plan uses a library SVD and OpenCV for feature matching and the five-point baseline.
- The evaluation starts with synthetic ground truth and measures rotation and translation-direction errors per frame pair. Reported results come from experiments the team has run.
- [data/](data/) holds local datasets. Copyrighted PDFs in `sources/` are kept out of Git.
