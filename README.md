# notes
All kinds of notes that thought to be useful.

[TOC]

# Math

## Gaussian kernel

**OpenCV**

```python
def gaussian_kernel_2d_opencv(kernel_size = 3,sigma = 0):
    kx = cv2.getGaussianKernel(kernel_size,sigma)
    ky = cv2.getGaussianKernel(kernel_size,sigma)
    return np.multiply(kx,np.transpose(ky))
```

**Numpy**

```python
def gaussian_2d_kernel(kernel_size = 3,sigma = 0):
    
    kernel = np.zeros([kernel_size,kernel_size])
    center = kernel_size//2
    
    if sigma == 0:
        sigma = ((kernel_size-1)*0.5 - 1)*0.3 + 0.8
    
    s = 2*(sigma**2)
    sum_val = 0
    for i in range(0,kernel_size):
        for j in range(0,kernel_size):
            x = i-center
            y = j-center
            kernel[i,j] = np.exp(-(x**2+y**2) / s)
            sum_val += kernel[i,j]
            #/(np.pi * s)
    sum_val = 1/sum_val
    return kernel*sum_val
```

