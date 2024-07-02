title: "Stereo Vision"
categories:
 - Comgong
---
#Stereo Vision : 네이버 블로그








​

**D**epth를 **측**정하기 **위**한 **방**법은 **다**양하게 **존**재한다.

​

* **레**이저 삼각측량(Laser triangulation)
* 비행시간 측정(TOF,Time-of-Flight)
* 구조광 방식(Structured light)
* 타임코드 구조광(Time-coded structured light)
* 적외선(IR)
* etc...

​

크게는 시간 영역(TimeDomain)과 공간 영역(SpatialDomain)으로 나뉘는데,

오늘은 공간 영역 중 Stereo Vision을 다룬다.

​

​

​





 



> 
> Stereo Vision 원리
> 
> 
> 에피폴라 기하학을 보면 Depth가 보인다!
> 
> 
> 









**스**테레오 비전은 간단하다.

​

**사**람이 물체를 바라 볼 때, **왼**쪽 눈과 **오**른쪽 눈이 바라보는 상이 다른 것은 당연히 알 것이다.

(모른다면 손으로 한쪽 눈을 가려보자..)

​

서로 다른 상은, 우리의 뇌(시각겉질)로 들어와, 물체의 경계, 크기, 그리고 거리(Depth)를 측정한다





 



[![](https://www.msdmanuals.com/-/media/manual/home/images/e/y/e/eye_tracing_visual_pathway_ko.gif?mw=704&thn=0&sc_lang=ko-kr)](#)








​

​

​

​

​

​

카메라를 사용한 Stereo Depth 측정 방법 또한 마찬가지이다.

​

대상 오브젝트를 일정한 거리를 두고 바라 본 뒤, 왼쪽 이미지와 오른쪽 이미지를 비교하여 거리를 측정한다

​

이 때, 두 이미지의 같은 점을 이은 선분을 **에피폴라 선(epipolar line)**이라고 한다. 단. 카메라가 가로축으로 평행해야 다른 픽셀의 에피폴라 선이 평행해지는데, 이를 **에피폴라 제약(Epipolar Constraint)**이라고 한다

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-12-21-Stereo Vision/1.png)](#)








당연하게도 가까운 오브젝트는 픽셀차가 크고, 먼 오브젝트는 픽셀 차가 작을 것이다.

​

이것이 StereoVision의 원리이다.

​

​

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-12-21-Stereo Vision/2.png)](#)








특정한 픽셀을 기준으로 그은 에피폴라 라인 ...

​

​





 



> 
> Stereo 거리 계산에 필요한 변수
> 
> 
> 









스테레오 거리를 계산하기 위한 변수들은 아래와 같다

​

BaseLine : 카메라와 카메라 사이의 거리이다

Disparity : 픽셀과 픽셀 간의 차이이다

Depth : 구하고자 하는 대상의 거리이다

Focal length in Pixel : 픽셀의 초점 거리이다

​

​

​

​

천천히 하나씩 설명하겠다





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-12-21-Stereo Vision/3.png)](#)








우선 **BaseLine**과 **Depth**는 간단하다. 말 그대로 카메라 사이의 거리와 대상과 카메라의 거리이다.

​

**Disparity**는 두 상의 같은 오브젝트의 픽셀 x1과 x2 사이의 거리이다.

​

당연하겠지만 오브젝트의 거리가 멀면 픽셀간 거리가 가까워지고

오브젝트의 거리가 가까우면, 두 픽셀간의 거리가 멀어지겠지

​

​

**Focal length in Pixel**는 픽셀의 초점 거리로, 물리적인 Focal length를 센서의 pixel에 맞춘 값이다. 주의할 점은 **Focal length**와는 다른 값인데, Focal length in Pixel과 Focal length는 비례하니 일단은 Focal length 라고 생각하고 계산식을 도출해보자(Focal length in Pixel에 대한 수식은 아래에서 설명)

​

​

​

​





 



> 
> 에피폴라 선을 이용하여 Depth를 구하기
> 
> 
> 









[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-12-21-Stereo Vision/4.png)](#)








대상 픽셀을 기준으로 Baseline과 수직으로 선을 그으면, 삼각형 네개를 그릴 수 있다.

​

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-12-21-Stereo Vision/5.png)](#)








당연하게도 왼쪽의 두 삼각형과 오른쪽의 두 삼각형은 비례하고, 가로와 세로를 이용하여 비례식을 만들 수 있다.

​

카메라에 비춰진 왼쪽이 픽셀 값이 xl, 오른쪽 픽셀 값이 xl이라 할 때,





 











이고 xl - xr = disparity이니,

​





 











가 성립한다.

​

​

​

​

단. 주의할 점은, 이 식은 카메라의 각도가 직각이였을때를 상정한다.

서로 다른 각도를 가진 카메라일 경우, 카메라의 외부행렬을 사용해야 한다.

​

각도가 달라지면 서로 겹지는 Disparity 가 상대적이기 때문에...

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-12-21-Stereo Vision/6.png)](#)








(각도가 포함된 외부행렬 계산은 아래 PDF를 참조)

<http://vision.psych.umn.edu/users/schrater/schrater_lab/courses/CompVis07/Papers/Stereo.pdf>

​

​

​





 



> 
> **Focal length in Pixel** 구하기
> 
> 
> 









Focal length in Pixel은, 우리가 실제 사용하는 값. 실제 해상도에 비례한 초점거리이다.

Focal length는 센서값과 관련이 없는 렌즈의 초점거리이고.

​

위에서 도출한 식의 단위는 





 




```
disparity [pixels] focal length [pixels]
------------------ = ---------------------
 baseline [mm] depth [mm]
```





 



이기 때문에, disparity[pixel]을 사용하기 위해서는

똑같이 focal length를 pixel에 비례한 값으로 바꿀 필요가 있다.

​

focal length를 pixel에 비례한 값으로 바꾸는 과정은, 캘리브레이션과 동일하다

​

<https://ch.mathworks.com/help/vision/ug/camera-calibration.html>

​

focasl length in pixel 값은

​

sensor pixels = 이미지 센서 픽셀 수(pixel)

focal length = 렌즈 초점거리(mm)

sensor size = 이미지 센서의 물리적 거리(mm)

​

으로 구할 수 있다

​





 











위 수식을 사용하는데,

​

보통 이미지 센서의 가로축이나 세로 축 아무거나 사용하면 된다.

​

ex) 가로 2590 pixel, 16mm렌즈, 센서가로 5.7mm이라면

​

focal length(pixel)은 7270.175438596491이 나온다.

​

사실 이렇게 계산하는 방법 말고도 focal length in pixel을 구하는 방법이 또 있는데,

​

openCV로 캘리브레이션을 하면 output으로 fx, fy값이 나온다.

​

fx,fy가 그대로 focal length in pixel 값이다.

​

카메라의 왜곡을 실제 물리적 값으로 바꾸기 때문에.. 같은 계산을 사용한다

​

다른 점이 있다면 opencv에서는 초점거리 input을 안넣고 체스판으로 캘리브레이션을 한다는 점?

​

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-12-21-Stereo Vision/7.png)](#)








openCV의 캘리브레이션..

​

​

​

이렇게 구한 focal length in Pixel값으로 실제 Depth를 계산 할 수 있다

​

​

​





 



> 
> StereoVision Dataset
> 
> 
> 









opencv의 스테레오 비전을 사용할때는 보통 아래 이미지 데이터셋을 사용 할 텐데





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-12-21-Stereo Vision/8.png)](#)








이 이미지는 실제 이미지가 아닌 3D시뮬레이터로 생성한 이미지이다.

​

​





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-12-21-Stereo Vision/9.png)](#)








​

따라서 카메라 왜곡도 보정되어 있고, 에피폴라 선(카메라 가로선)도 정확하게 맞으므로, Depth 결과가 잘 나온다

​

데이터셋 링크:

<https://home.cvlab.cs.tsukuba.ac.jp/dataset>





 



[![](https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Flh5.googleusercontent.com%2FircPEiGiZ0wYOxJNNPfQA6GlRY9528NGyAzulJKN7GyVSUaQ6YPdbS2vpq7INolhbNA_nA%3Dw16383%22&type=ff120)](https://home.cvlab.cs.tsukuba.ac.jp/dataset)
[**CVLAB Homepage - Dataset**
NEW TSUKUBA STEREO DATASET


home.cvlab.cs.tsukuba.ac.jp](https://home.cvlab.cs.tsukuba.ac.jp/dataset)




 



​

​





 



> 
> openCV StereoBM, StereoSGBM 이론 설명
> 
> 
> 









실제 Depth를 계산하기 위해서는 직접 픽셀을 골라 disparity를 구해도 되지만, openCV에서 기본으로 제공하는 알고리즘인 StereoBM과 StereoSGBM을 사용하겠다.

​

우선 StereoBM은 한 픽셀을 기준으로, 인접한 유사한 픽셀을 찾는다.





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-12-21-Stereo Vision/10.png)](#)








인접한 유사한 픽셀을 찾을 땐 SAD매칭 방법을 사용한다.

​

SAD는 Sum-of-Absolute-Diffrences으로, 말 그래도 왼쪽 이미지와 오른쪽 이미지의 에피폴라 선을 따라서, 특정 블록을 합산 한 후, 정합하여 같은 픽셀을 찾는다.





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-12-21-Stereo Vision/11.png)](#)








후에 설명할 StereoSGBM보다 빠르지만, 바라보는 대상 A와 B의 Depth차이가 클 경우, Disparity 매칭이 잘 되지 않을 수 있다는 단점이 있다.

​

​

StereoBM paper:

<https://www.researchgate.net/publication/251949538_Sum_of_Absolute_Differences_algorithm_in_stereo_correspondence_problem_for_stereo_matching_in_computer_vision_application?_tp=eyJjb250ZXh0Ijp7ImZpcnN0UGFnZSI6InB1YmxpY2F0aW9uIiwicGFnZSI6InB1YmxpY2F0aW9uIn19#read>

​

Very fast SAD-based (Sum-of-Absolute-Diffrences) stereo correspondence algorithm.논문에서 Matlab으로 구현한 코드를 Kurt Konolige가 [OpenCV 코드](https://github.com/opencv/opencv/blob/master/modules/calib3d/src/stereobm.cpp)를 작성하였다.

​

​

​

StereoSGBM은 위에서 이미지 두개의 전역적인 이미지 offset이 아닌, 각 픽셀별로 매칭되는 픽셀을 찾는 방식이다. SG는 Semi-Global이다. SGBM에서는 각 픽셀별로 이미지를 매칭시키므로, 계산량이 비약적으로 증가한다. 

​

효과적인 예로는 푸쉬브룸(pushbroom)이미지가 있다.





 



[![](https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-12-21-Stereo Vision/12.png)](#)








항공 사진 특성상, 지표면이 일정하지 않으니 픽셀별로 에피폴라 선이 달라지게 되는데, 각 픽셀마다 Disparity를 계산하므로, 높은 정확도를 보여 줄 수 있다.

<https://core.ac.uk/download/pdf/11134866.pdf>

​

​

​

​

​





 



> 
> openCV StereoBM, StereoSGBM 코드 설명
> 
> 
> 









Class Document

<https://docs.opencv.org/3.4/dd/d53/tutorial_py_depthmap.html>





 



[![](https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fdocs.opencv.org%2F3.4%2Fstereo_depth.jpg%22&type=ff120)](https://docs.opencv.org/3.4/dd/d53/tutorial_py_depthmap.html)
[**OpenCV: Depth Map from Stereo Images**
Goal In this session, We will learn to create a depth map from stereo images. Basics In the last session, we saw basic concepts like epipolar constraints and other related terms. We also saw that if we have two images of same scene, we can get depth information from that in an intuitive way. Below i...


docs.opencv.org](https://docs.opencv.org/3.4/dd/d53/tutorial_py_depthmap.html)




 



<https://docs.opencv.org/3.4/d9/dba/classcv_1_1StereoBM.html>





 



[![](https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fdocs.opencv.org%2F3.4%2Fd9%2Fdba%2Fclasscv_1_1StereoBM.png%22&type=ff120)](https://docs.opencv.org/3.4/d9/dba/classcv_1_1StereoBM.html)
[**OpenCV: cv::StereoBM Class Reference**
Class for computing stereo correspondence using the block matching algorithm, introduced and contributed to OpenCV by K. Konolige. More... #include <opencv2/calib3d.hpp> Inheritance diagram for cv::StereoBM: Public Types enum   { PREFILTER\_NORMALIZED\_RESPONSE = 0, PREFILTER\_XSOBEL = 1 }  Public Type...


docs.opencv.org](https://docs.opencv.org/3.4/d9/dba/classcv_1_1StereoBM.html)




 



<https://docs.opencv.org/3.4/d2/d85/classcv_1_1StereoSGBM.html>





 



[**OpenCV: cv::StereoSGBM Class Reference**
The class implements the modified H. Hirschmuller algorithm [104] that differs from the original one as follows: More... #include <opencv2/calib3d.hpp> Inheritance diagram for cv::StereoSGBM: Public Types enum   { MODE\_SGBM = 0, MODE\_HH = 1, MODE\_SGBM\_3WAY = 2, MODE\_HH4 = 3 }  Public Types inherited...


docs.opencv.org](https://docs.opencv.org/3.4/d2/d85/classcv_1_1StereoSGBM.html)




 



​

​

이하 작성중...

​

​

​

​

​

​

​

​

​

​

​

​

​

​

​

모든 픽셀의 에피폴라 선이 평행하다면 좋겠지만... 카메라 렌즈의 왜곡, 물리적으로 미세한 각도, 높이 차 때문에 

​

1. 카메라 


	1. 명암 대비를 높이기 위해 감마를 낮게 설정
	2. 피사계 심도를 올리기 위해 조리개를 조임
	3. 형광등의 noise감소를 위해 fps고정
	4. 센서에 더 많은 빛을 받도록 exposure를 최대
	5. 밝거나 어두운 부분에서도 대비되는 픽셀을 가지기 위해 조리개 조정
	6. 픽셀 대비를 가지기 위해 히스토그램의 표준편차가 높아지게 조리개 조정
	7. fov가 높을 경우, 캘리브레이션 적용
2. 대상 


	1. 재질 
	
	
		1. 찍기 좋은 대상은, 굴곡이 많고, 무늬가 있으며 난반사가 많이 일어나는 오브젝트
		2. 찍기 어려운 대상은, 빛이 반사되거나 흡수되어, 면적의 픽셀값 차이가 거의 없는 오브젝트
3. 광원 


	1. 오브젝트의 그림자에서는 특징 검출이 어렵기 때문에, 그림자가 지지 않는 각도를 설정한다
	2. (제안)오브젝트의 특징점을 만들기 위해 레이저나 특정 패턴의 광원을 사용한다 기존의 일반 광원은 오브젝트 자체의 난반사를 이용하지만, 오브젝트의 표면이 매끄럽다면, 픽셀 검출이 어렵다. 따라서 직진성이 강한 레이저나 특정 패턴을 쏘고, 패턴이 오브젝트에 맺힌 상을 이용하여 특징 검출을 하는 것이 유효할 것으로 보인다
	3. (제안)오브젝트의 표면이 매끄럽더라도, 사선에서 빛을 비추면 카메라에서 받는 픽셀 값이 다르므로 검출이 가능 할 것이다
4. 전처리 


	1. sharpness
	2. midian blur
	3. gaussian blur
5. 후처리 


	1. wls filtter <https://docs.opencv.org/3.4/d3/d14/tutorial_ximgproc_disparity_filtering.html>

​

​

​

​