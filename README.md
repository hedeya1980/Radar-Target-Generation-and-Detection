- **Implementation steps for the 2D CFAR process:**
  - Sliding the CUT across the locations of the RDM matrix, while keeping the training and guard margins. This was achieved by the for loops on lines 192:195.
  - Updating the noise level from the signal values on the training cells.
  - Taking the average of the noise level by dividing on the total number of the training cells.
  - Adding the offset required to achieve the desired SNR. This is the value that's used for thresholding.
  - Updating the signal\_cfar mask by setting the value of the locations where the signal level is more than the threshold value to 1.
- **Selection of Training, Guard cells and offset:**
  - I used the following values for the Training, Guard cells, and the offset (the same values that were used in the project video):
    - Tr=10, Td=8
    - Gr=Gd=4
    - Offset=6
- **Steps taken to suppress the non-thresholded cells at the edges:**
  - This was achieved as follows:

1. Properly choosing the start and end values of the for loops as follows:
  1. Range: "Tr+Gr+1" to "m-(Gr+Tr)"
  2. Doppler: "Td+Gd+1" to "n-(Gd+Td)"
2. Initializing the signal\_cfar variable to zeros, and setting only the locations where the signal is more than the threshold to 1.