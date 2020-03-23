# trial
First Git repo for trial

---
## Intent
Serve as a Guide for anyone to implement or reproduce https://github.com/marvis/pytorch-yolo2 on local computer.  These instructions and steps were performed on a Desktop computer with following specs:
- CPU: Intel(R) Core(TM) i7-8700 CPU @ 3.20GHz
- RAM: 16GB
- OS : Ubuntu 19.04 disco 64-bit

### Need for this document
- The https://github.com/marvis/pytorch-yolo2 was originaly implemented and documented for Python 2 
  - This document assume use of Python 3
- Some links to source data (i.e. pjriddie darknet) have changed over time and our reference git ('marvis') has **not** been updated

### Enviornment
This document assume use of an enviornment manager to ensure proper version of various tools/softwares. 
  - This guide was developed with use of Conda / Anaconda <sup>5</sup>
- Some specific software version used for this guide:

Software    | Version
----------- | --------
conda       | 4.8.3 
python      | 3.7.4
pytorch     | 1.3.1
torchvision | 0.4.2
numpy       | 1.17.2
pandas      | 1.0.2
opencv      | 4.1.0
pillow      | 6.1

---
## Implementation Steps

- [x] `git clone https://github.com/marvis/pytorch-yolo2`
  - Clone the Git repository to your local computer. If unfamiliar with Git, please refer to *1* and *2* references mentioned at end of this document
- [x] `cat *.patch | git am`
  - Apply the provided patch file(s) and modify the code to run with latest software versions (such as the ones mentioned above)
    - If you are unfamiliar with Git patches, please consult online resources <sup>3</sup>
  - Alternatively, You can make the code changes manually as follows:
    - Open the patch file(s) in any text editor (*Tool Tip: Sublime is powerful GUI based editor*)
    - Read the diff / changes for each file <sup>4</sup>
    - Modify each file individually
    - Save and Compile regularly 

- Follow the detailed steps listed on https://github.com/marvis/pytorch-yolo2. High Level steps with some important notes and changes : 
  - [x] Perform detection on Static Image File(s) 
  ```
  wget http://pjreddie.com/media/files/yolo.weights
  python detect.py cfg/yolo.cfg yolo.weights data/dog.jpg
  ```
  - [x] Perform detection on Video : `python demo.py cfg/tiny-yolo-voc.cfg tiny-yolo-voc.weights`
    - **NOTE** The origianl code is assuming presence of a webcam 
    - However, the patch modifies the code to work on an .mp4 video file (any other video file format that is accepted by OpenCV would also work)
      - File name "demo.py" : line `cap = cv2.VideoCapture('./data/office-parkour-caps.mp4')` 
      - *IMP* : Please replace the video file path as avialable on Your system 
  - Perform training on local computer
    - This may or may not work on local computer - depends on computer hardware capability (RAM, GPU availability, etc.)

---
#### Online Resources and Links
1. Git Intro : https://thenewstack.io/tutorial-git-for-absolutely-everyone/ 
2. Git Cheat Sheet (PDF) : https://education.github.com/git-cheat-sheet-education.pdf 
3. Git Patches Use Example: https://thoughtbot.com/blog/send-a-patch-to-someone-using-git-format-patch 
4. Understanding Git Patches : https://www.oreilly.com/library/view/git-pocket-guide/9781449327507/ch11.html
5. Anaconda / Conda Info: https://www.anaconda.com/distribution/ 
