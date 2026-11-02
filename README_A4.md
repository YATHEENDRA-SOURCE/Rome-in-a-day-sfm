# ES666 Assignment 4: Rome in a Day

**Name:** Gurijala Yatheendra Reddy
**Roll number:** 26210053

Structure from Motion at city scale: starting from about 9,000 unlabelled tourist photos of Rome,
the pipeline finds which photos show the same place, matches points between them and rebuilds
landmarks like the Trevi Fountain and St Peter's in 3D. Task 10 runs the same pipeline on my own
photos of a campus building (AB 13).

## What I implemented

| Function | What it does |
|---|---|
| `tfidf_matrix` | Turns each photo into a weighted list of visual words |
| `top_k_neighbours` | Finds the most similar photos for each photo |
| `match_descriptors` | Matches keypoints between two photos (ratio test + mutual check) |
| `query_expansion` | Suggests new pairs through shared neighbours |
| `connected_components` | Groups photos into landmarks |
| `homography_dlt` | Fits a homography with the normalised DLT |
| `homography_ratio` | Tests whether a pair has real parallax (H vs F inliers) |
| `triangulate_points` | Finds 3D points from two views |
| `umeyama` | Aligns two 3D maps (scale, rotation, shift) |

All 89 checks pass and the notebook runs from top to bottom with no errors.

## Results

| | |
|---|---|
| Trevi Fountain | 508 of 528 photos placed, 0.73 px error, 842,771 dense points |
| St Peter's | two maps merged with 407 anchors |
| Task 10: AB 13 (my own photos) | 65 of 65 photos placed, 0.95 px error, 280,770 dense points |

## Files

```
26210053_rome_in_a_day.ipynb     the notebook, run from the top with all outputs
toolbox/                         provided course code
rome_from_folder.py              provided script used for Task 10
task10_ab13/
    photos/26210053_AB13_photos_65.zip   my 65 photos (resized copies)
    results/                             dense.ply, sparse.ply, view.html, cameras.csv, summary.txt
pipeline_sheet_26210053.jpeg     hand drawn pipeline sheet
```

Open `task10_ab13/results/view.html` in a browser to rotate the 3D model of AB 13.

The Rome dataset (`mini_rome.zip`, about 580 MB) is not stored here; the notebook downloads it
from the course release when it runs.
