#### 腐蚀/膨胀/开运算/闭运算/顶帽/黑帽

> [车牌例子](https://blog.csdn.net/wsh596823919/article/details/79982485)

1. 图像腐蚀
----
腐蚀基本思想： 腐蚀前景色物体的边界（总是视图保持前景色为白色）；内核在图像中滑动（如：在2D卷积中）只有当内核下的所有像素都是1时候，原始图像中像素（1或者0）才会被认为是1，否则它会被腐蚀（为0）

边界附近的所有像素都将被丢弃，具体取决于内核的大小，前景对象的厚度或者大小，或者图像中白色区域减小，它有助于去除小的白色噪声，分离链接的对象
```python
        import cv2
        import numpy as np
        img = cv2.imread("example.png",0)

        kernel = np,ones((6,6),np.uint8)
        erosion = cv2.erode(img,kernel,iterations = 1)

        cv2.imshow("test",img)
        cv2.imshow("show",erosion)
        cv2.waitKey(0)

```

2. 图像膨胀
----
与腐蚀相反，如果内核下至少一个像素为1，则像素元素为1。因此它增强了图像中白色区域的前景对象大小。

通常，再去除噪音的情况下，腐蚀之后是膨胀。因为，腐蚀会去除白噪声，但也会缩小我们的物体，所以我们膨胀它，由于噪音消失了，我们的物体区域会增加，它也会用于***链接对象的破碎部分***。
```py
        import cv2
        import numpy as np
        img = cv2.imread("example.png",0)

        kernel = np.ones((6,6),np.uint8)
        dilation = cv2.dilate(img,kernel,iterations = 1)

        cv2.imshow("test",img)
        cv2.imshow("show",dilation)
        cv2.waitKey(0)
```
3. 开运算
----
`cv2.morphologyEx()`：先腐蚀再膨胀，有助于消除噪音

```py
        import cv2
        import numpy as np
        import matplotlib.pylab as plt

        img = cv2.imread("test.png",0)

        kernel = np.ones((6,6),np.uint8)
        opening = cv2.morphologyEx(img,cv2.MORPH_OPEN,kernel)

        cv2.imshow("test",img)
        cv2.imshow("show",opening)
        cv2.waitKey(0)
```
4. 闭运算
----
`cv2.morphologyEx()`: 先膨胀后腐蚀，用于消除前景对象内的小孔或者对象上的黑点
```py
        import cv2
        import numpy as np

        img = cv2.imread("test.png",0)

        kernel = np.ones((6,6),np.uint8)
        closing = cv2.morphologyEx(img,cv2.MORPH_CLOSE,kernel)

        cv2.imshow("test",img)
        cv2.imshow("show",closing)
        cv2.waitKey(0)
```
5. 形态学梯度
----
图像的膨胀和腐蚀之间的差异，结果看起来像目标的轮廓
```py
        import cv2
        import numpy as np

        img = cv2.imread("test.png",0)

        kernel = np.ones((6,6),np.uint8)
        gradient = cv2.morphologyEx(img,cv2.MORPH_GRADIENT,kernel)

        cv2.imshow("test",img)
        cv2.imshow("show",gradient)
        cv2.waitKey(0)
```

6. 顶帽
----
原图像与开运算的区别，突出原图像比周围亮的区域

```
        import cv2
        import numpy as np

        img =  cv2.imread('test.png',0)

        kernel = np.ones((6,6),np.uint8)
        tophat = cv2.morphologyEx(img,cv2.MORPH_TOPHAT,kernel)

        cv2.imshow("test",img)
        cv2.imshwo("show",tophat)
        cv2.waitKey(0)
```

7. 黑帽
比运算图像 - 原图像，突出原图像中比周围暗的区域
```py
        import cv2
        import numpy as np

        img = cv2.imread("test.png",0)

        kernel = np.ones((6,6),np.uint8)
        blackhat = cv2.morphologyEx(img, cv2.MORPH_BLACKHAT,kernel)

        cv2.imshow("test",img)
        cv2.imshwo("show",blackhat)
        cv2.waitKey(0)
```



