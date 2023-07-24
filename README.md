# LNDb_detection
Objective: LNDb preprocessing and tumor detection  
  
LNDb has different numbers of segmentations by multiple radiologists for each CT lung scan.  
One can choose either voting, union, or intersection to conclude what the ground truth looks like.  
  
Personally, the voting and union segmentations looked more promising due to the difficulty of finding small tumors with the human eye.  
That would reduce the number of false "False Positives" (labeled as FP when it should be TP).  

Another issue was grouping the different tumors in each scan.  
The segmentations in LNDb are imperfect; some tumors are labeled as the same based on proximity, while others are labeled based on adjacency.  
bfs_voting_seg.ipynb strictly uses adjacency for grouping, but it is farther from the ground truth.  
voting_seg.ipynb uses a 3D (cubic) sliding window to group tumors based on proximity, and this minimizes errors.  

visualize_masks.ipynb draws white bounding boxes around each predicted tumor in the validation stage.  
The nifti file outputs can be used to evaluate model performance, with varying thresholds of confidence.  
