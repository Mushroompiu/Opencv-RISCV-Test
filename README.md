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

## Save the result to the current folder named diff.jpg
```
cv2.imwrite(r'.\diff1.jpg', change)
```
## Show
```
cv2.imshow('diff', change)
```

# Timers in RISCv
There are two basic interrupt controllers on riscv, aclint and plic, the former is the full name of Advanced Core Local Interruptor, is the interrupt controller within the core, mainly used to generate timer interrupts and software interrupts, the latter is the full name of Platform Level Interruptor Controller, mainly used to collect interrupts from peripherals. plic reports interrupts to the CPU through external interrupts.

The timer-related registers and register fields are: mip/mie, mtime, and mtimecmp.
In mie, there are bits that control timer interrupt enable: MTIE/STIE, and whether M mode and S mode timer interrupter are enabled. mip has bits that indicate whether there is a pending timer interrupt: MTIP/STIP.

mtime is a read-write counter, the value of which is incremented at certain time intervals, the counter will rewind when it is full. mtimecmp register value is used to compare with mtime, when the value of mtime is greater than or equal to the value of mtimecmp, and MTIE is enabled, M mode timer interrupter is triggered.

Software can update the value of mtimecmp in the timer interrupt handler function to maintain a fixed period of the clock interrupt, generally this interrupt is the Linux kernel clock interrupt. Software can write STIP to trigger an S mode timer interrupt

[Generic RISC-V SoC platform](https://github.com/cnrv/riscv-notes/blob/master/architecture/platform.md#generic-risc-v-soc-platform)

