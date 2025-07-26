Our objective is to maximize crater and boulder detection on the lunar surface using Chandrayaan-2's Orbiter High-Resolution Camera (OHRC) imagery. We have manually labelled OHRC images, identifying center coordinates, height, and width of
bounding boxes of craters and boulders. This identification relies on shadows and sun direction, with darker and brighter regions present for features opposite the sun's direction. Boulders protrude from the surface, casting shadows and often appearing in
clusters, while craters exhibit smoother floors compared to surrounding terrain.

Initially, we employed YOLO and Faster R-CNN for object detection. However, these methods yielded low confidence (<50%) in detecting craters and identified very few boulders. To address this, we have developed an innovative solution combining
YOLO with SAHI (Slicing Array Hyper Interference). Our approach first divides each large OHRC image (~7500x1200 px) into approximately 24 smaller (640x640 px) images to enhance accuracy. We then label these images for craters and
boulders using Roboflow.

Our two-stage detection process begins by training YOLO on these smaller images to improve upon the pre-trained model. Subsequently, we apply SAHI to detect even smaller objects within our images. This combined YOLO+SAHI approach
significantly improves detection capabilities with high confidence (>50%), as demonstrated in our qualitative estimation shown in
subsequent slides. After training YOLO, SAHI can be applied directly to the large original images for comprehensive detection.

Furthermore, we utilize the grid.csv file provided with OHRC images and the normalized labels generated from test data to
quantify the selenographic position of each detected craters and boulders and hence determining the radius of the craters and
boulders.
