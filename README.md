# gaia-stream-gaps
Gaia DR3 pipeline for detecting dark-matter-subhalo gaps in Milky Way stellar streams (GD-1, Palomar 5, Jhelum), with a parallax-contamination diagnostic and IllustrisTNG50-1 cross-check.


An end-to-end pipeline that queries live Gaia DR3 data, selects stream members via proper-motion and color-magnitude cuts, and searches for density gaps that indicate perturbation by low-mass dark matter subhalos. Applied to GD-1, Palomar 5, and Jhelum, it recovers one candidate gap (Jhelum) and two null results, cross-validated against an independent parallax-distance contamination check and a filter-verified IllustrisTNG50-1 subhalo comparison. Built as a self-directed, real-data computational astrophysics project.

This pipeline searches for density gaps in Milky Way stellar streams that may indicate perturbation by low-mass dark matter subhalos. It runs end-to-end on live-queried Gaia DR3 data with no manual intervention between query and result.

Stages:

Data acquisition: queries the Gaia DR3 archive (with automatic fallback to a mirror if the primary archive is unreachable) for a spatial region around each target stream.
Kinematic selection: applies a Mahalanobis-distance cut in proper-motion space to isolate stars consistent with the stream's published track.
Photometric refinement: applies a color-magnitude matched-filter cut using real Gaia BP−RP photometry, fitting a ridge line from a high-confidence subsample to reject residual field contamination the kinematic cut alone misses.
Coordinate transformation: rotates each selected sample into its published stream-aligned coordinate frame and cuts to a narrow backbone around the stream track.
Gap detection: builds a cross-validated Gaussian KDE density profile along the stream, compares it against a fitted polynomial background, and assesses gap significance via non-parametric bootstrap.
Independent validation: cross-checks any candidate gap against a Gaia parallax zero-point-corrected distance estimate, to flag samples where kinematic/photometric selection alone left residual foreground contamination.
Simulation comparison: cross-matches any detected gap mass against the public IllustrisTNG50-1 subhalo catalog, with a control-query step that validates the API's mass filter before trusting results.

Inputs: stream name, sky region, published stream-frame parameters.
Outputs: selected member catalog, density profile with gap significance, parallax-distance diagnostic, TNG50-1 mass comparison.
