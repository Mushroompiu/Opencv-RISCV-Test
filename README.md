# Opencv-RISCV-Test

# How to implement Opencv on RiscV

[Optimizing OpenCV for the RISC-V Architecture](https://opencv.org/optimizing-opencv-for-the-risc-v-architecture/)

[Running OpenCV on RISC-V CPUs](https://github.com/opencv/opencv/wiki/OpenCV-RISC-V)


# Image change detection - Difference method

```
import cv2
```

## Read image
```
img1 = cv2.imread(r'.\pic\atl_spotp_87.jpg')  
img2 = cv2.imread(r'.\pic\atl_spotp_92.jpg')
```

## absdiff To acquire a difference map is to make a difference between two images
```
change = cv2.absdiff(img1, img2)
```

##Save the result to the current folder named diff.jpg
```
cv2.imwrite(r'.\diff1.jpg', change)
```
##Show
```
cv2.imshow('diff', change)
```

