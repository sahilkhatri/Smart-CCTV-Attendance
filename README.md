# Smart-CCTV-Attendance
In this project I have created a CCTV based attendance system. This can help to take attendance and monitor the movements of the employees/students in the premise.

This repo contains 3 files. 
1. datasetgather.py
2. create_encodings.py
3. main.py

For conveniency create a directory with following hierarchy:
-Smart CCTV Attendance
  -images (images gathered from the video are to be stored in this folder)
    -xyz
      -frame1.jpg     (This jpg's will be created by datasetgather.py.)
      -frame2.jpg
      .
      .
    -abc
      -frame1.jpg     (This jpg's will be created by datasetgather.py.)
      -frame2.jpg
      .
      .
  -videos (video of the person needs to be stored in this folder)
    -xyz.mp4
    -abc.mp4
  -encoding-names (this folder will contain the encodings of the images and its corrosponding names)
  -create_endodings.py
  -datasetgather.py
  -main.py
(view this hierarchy in raw form)
  
Firstly, put the video of the perso need to be detected inside the "videos" folder. This video should contain only the face of the person.
Store the video with the name of the person as file name. For example if name of the person is "xyz", then store the video xyz.mp4 in the
"videos" directory

After that, run the datasetgather.py file to generate frames from the video, and store them insde the "images" folder. You need to create a 
folder with name of the person. And give its path in the datasetgather.py file, which will store the corresponding images.

Now, we need to create the encodings of the face in the images. For this execute the create_encodings.py. This file will take all the images
from the "images" directory, and creates the embeddings. It also stores the corresponding subdirectory name as label (to identify which image
belongs to which person). The encodings and labels pickle file are then stored in the "encoding-names" folder.

Finally, when we execute the main.py file, it will load the stored encodings and labels. It will take the live feeds from the CCTVs, and
recognizes the person present. This data is then dumped in the database. Here, we have also used the parallel processing for each camera 
feed, this helps to gain better performance.
