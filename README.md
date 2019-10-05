# Course-OpenCV

## 安装opencv

下载压缩包，默认下载是最新的4.0.0，我下的是3.4.3
在目录/Users/your_user_name/opencv下解压，则解压后opencv文件夹位置为/Users/your_user_name/opencv/opencv-3.4.3
安装cmake, brew install cmake
在/Users/your_user_name/opencv/opencv-3.4.3新建文件夹build
进入文件夹build, cd build，利用cmake编译，cmake -G "Unix Makefiles" ..
完成上一步后，make -j8
之后，sudo make install
配置Xcode

进入Xcode，新建一个project，选择Command Line Tool
点击next, 输入项目名称，选择c++语言
设置Xcode，使得编译器能够找到opencv library

![](https://ipic-1259722072.cos.ap-beijing.myqcloud.com/jymq8.jpg)

4. 测试代码：


```C++
#include <iostream>
#include "opencv2/highgui/highgui.hpp"
#include "opencv2/imgproc/imgproc.hpp"
#include "opencv2/core/core.hpp"
#include "opencv2/video/video.hpp"
#include "opencv2/imgcodecs/imgcodecs.hpp"

using namespace cv;
using namespace std;


int main()
{
    Mat image=imread("/Users/apple/Desktop/chris.jpg");
    //cv::imwrite("/Users/apple/Desktop/haha.jpg", image);
    //cv::namedWindow("window",CV_WINDOW_AUTOSIZE);
    imshow("image", image);
    
    
    waitKey(0);
    //cout<<image<<endl;
    return 0;
}
```

写下代码之后，还要注意把相应的opencv library放在project中，这些library就在`/Users/your_user_name/opencv/opencv-3.4.3/build/lib`中。右键项目名称，然后选择`Add files to`进行添加

![](https://ipic-1259722072.cos.ap-beijing.myqcloud.com/8uwv5.jpg)

然后运行，会遇到Undefined symbols for architecture x86_64: "cv::imshow(cv::String const&, cv::\_InputArray const&)", referenced from: \_main in main.o问题，解决方法：[参考链接](https://stackoverflow.com/questions/34340578/installing-c-libraries-on-os-x)

![](https://ipic-1259722072.cos.ap-beijing.myqcloud.com/ds6zo.jpg)

```
-lopencv_calib3d
-lopencv_core
-lopencv_features2d
-lopencv_flann
-lopencv_highgui
-lopencv_imgproc
-lopencv_ml
-lopencv_objdetect
-lopencv_photo
-lopencv_stitching
-lopencv_superres
-lopencv_ts
-lopencv_video
-lopencv_videostab
```