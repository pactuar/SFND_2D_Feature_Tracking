1. The data buffer was implemented by deleting the first element of the vector then pushing the next element onto the end (to always keep the size at 2).

2. All 5 additional detectors were implemented. For Harris the threshold was changed to 30 as it was in the exercises. All others were implemented with default parameters.

3. Keypoints were removed by looping over all keypoints and deleted anything that wasn't in the rectangles bounds.

4. All 5 additional descriptors were implemented. Default settings were used.

5. FLANN matching was implemented. KNN was also implemented.

6. The KNN matching is filtered by the descriptor distance ratio test (threshold of 0.8).

*NOTE: For the performance numbers below. All cases were run on a local VM and not the workstation.*

7. Number or keypoints found by the detectors.  See spreadsheet for full details. Averages over all ten images given below:

    * SHITOMASI:   1342 (Lots of point on road and other car)
    * HARRIS:      77.5 (low number of keypoints, had to have a high threshold to get decent keypoints)
    * SIFT:        1356
    * FAST:        1787
    * ORB:         500
    * AKAZE:       1343

8. Number of of matches keypoints (Image pair 1 and 2) [I didn't do every combination for ALL ten images since that would be over 300 datapoints]

    * SHITOMASI + BRISK:    85
    * HARRIS + BRISK:       9
    * SIFT+BRISK:           57
    * FAST+BRISK:           149
    * ORB+BRISK:            73
    * AKAZE+BRISK:          137
    * AKAZE+AKAZE:          138
    * ORB+ORB:              67
    * ORB+FREAK:            42
    * ORB+BRIEF:            49
    * FAST+BRIEF:           119

9. Performance [detector (ms), descriptor (ms)] (Image pair 1 and 2) [I didn't do every combination for ALL ten images since that would be over 300 datapoints], so I chose a sample set to try

    * SHITOMASI + BRISK:    8.9, 1.4
    * HARRIS + BRISK:       88.6, 0.8
    * SIFT+BRISK:           85.6, 1.0
    * FAST+BRISK:           0.6, 1.6
    * ORB+BRISK:            4.4, 1.0
    * AKAZE+BRISK:          55.5, 1.18
    * AKAZE+AKAZE:          44.8, 34.9
    * ORB+ORB:              4.8, 2.1
    * ORB+FREAK:            4.9, 22.2
    * ORB+BRIEF:            4.5, 0.3
    * FAST+BRIEF:           0.6, 1.1

    Based on speed I would choose FAST+BRIEF, but I though the keypoint matches were a bit better with ORB. So my top 3 are:
    
    * ORB+ORB
    * ORB+BRIEF
    * FAST+BRIEF
