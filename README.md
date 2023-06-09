# Face-Mask-Detection
Real-time Face Mask Detection
Overview
Face masks help reduce the transmission of SARS-CoV-2 by interfering with the spread of virus-laden droplets ejected from the nose and mouth. Wearing face mask is one of the precautionary steps an individual can take in order to lessen the spread of COVID-19. In this simple project, a video camera detects if an individual is wearing a face mask or not in real-time.
The detection steps looks somewhat like this: 

Quickstart the project
Download the code in ZIP or open with GitHub Desktop or git clone https://github.com/Shrii0807/face-mask-detection.git. If you face issues downloading weight file, you can download from this google drive link.
Install required python dependencies into your python environment / virtual environment using pip install -r requirements.txt.
Run script-1.py for real-time detection using webcam. If detection isn't to your liking, try running script-2.py.
Dataset
The dataset used to train the face-mask detection model taken from here.

This dataset contains 853 images belonging to the 3 classes, as well as their bounding boxes in the PASCAL VOC format. The classes are:

With mask
Without mask
Mask worn incorrectly


Though the dataset is pretty imbalanced with most of the data belonging to With mask class, it works pertty well detecting With mask and Without mask classes. But more data for Mask worn incorrectly class is needed in order to detect this class properly.

Workflow
Data preprocessing : All images have their bounding boxes in the PASCAL VOC format and their info saved in XML format in annotaions directory. Only the region bounded by bounding box taken as input and their respective labels taken as output.

Training mask detector model : Transfer learning was used to train the inputs. The classifier model was built with InceptionV3 neural network architecture. After training for 20 epochs, accuracy on test set was 96.81%.

Detecting face mask in real-time : First task was to detect faces from each frame of the video. At first I used Haarcascade classifer from OpenCV for face detection. Average FPS I got while running on my machine was around 16. But face detection wasn't that accurate. This classifer struggled detecting faces with mask. In low-light condition it struggled the most.
Then I tried MTCNN for face detection. This algorithm performed great detecting faces, even in the low light. But while running on my machine, the average FPS I got was about 1.4. Which is pretty slow comparing with haarcascade classifier.

Results
Input	Output
	
Links and References
Face Mask Detection dataset: https://www.kaggle.com/andrewmvd/face-mask-detection
InceptionV3: https://www.tensorflow.org/api_docs/python/tf/keras/applications/InceptionV3
Face Detection using Haar Cascades: https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_objdetect/py_face_detection/py_face_detection.html
How to Perform Face Detection with Deep Learning: https://machinelearningmastery.com/how-to-perform-face-detection-with-classical-and-deep-learning-methods-in-python-with-keras/
