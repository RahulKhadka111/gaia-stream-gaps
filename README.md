# gaia-stream-gaps
Gaia DR3 pipeline for detecting dark-matter-subhalo gaps in Milky Way stellar streams (GD-1, Palomar 5, Jhelum), with a parallax-contamination diagnostic and IllustrisTNG50-1 cross-check.


An end-to-end pipeline that queries live Gaia DR3 data, selects stream members via proper-motion and color-magnitude cuts, and searches for density gaps that indicate perturbation by low-mass dark matter subhalos. Applied to GD-1, Palomar 5, and Jhelum, it recovers one candidate gap (Jhelum) and two null results, cross-validated against an independent parallax-distance contamination check and a filter-verified IllustrisTNG50-1 subhalo comparison. Built as a self-directed, real-data computational astrophysics project.
