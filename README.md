# 3D-Reconstruction-Note
三维重建有一个通用的框架：

1. 任意模态的信息(相机、Lidar、RGBD)作为输入

2. 通过算法(比如[SFM](docs/SFM/SFM.ipynb)、VSLAM、MVS)得到点云 + 图像(纹理) + 相机参数

3. 点云预处理 + 曲面重建 + 纹理贴图

本仓库介绍点云预处理，曲面重建，纹理贴图的内容。

## 一、点云预处理
[点云预处理](docs/pointcloud_preprocessing/pre_processing.ipynb)包括点云滤波，点云平滑(点云重采样)，和点云法线估计。

## 二、点云曲面重建
根据重建曲面和数据点云之间的关系可以将点云曲面重建分为两大类：插值法和逼近法，插值法得到的重建曲面**完全通过**原始数据点，而逼近法则是用分段线性曲面或其它形式曲面来**逼近**原始数据点。
此外还可以根据点云处理方式进行分类，比如先将点云转为深度图、体素再进行曲面重建。

1. 利用深度图+体素曲面重建(逼近法)：[SDF+TSDF+MC](docs/surface_reconstruction/TSDF.ipynb)
2. 利用点云曲面重建(插值法)：[Convext Hull, Ear Clipping, Greedy Projection Triangulation algorithm](docs/surface_reconstruction/pointMeshing.ipynb)
3. 利用点云曲面重建(逼近法)：[Poisson reconstruction](docs/surface_reconstruction/Poisson.md)、[B样条曲面重建](docs/surface_reconstruction/Bspline.ipynb)

注意：在这些算法中，TSDF+MD是唯一online的算法，其它都是offline算法。

## 三、曲面贴图
曲面重建完成后可以通过曲面顶点与图像的对应关系(点像对应)给网格加上颜色生成彩色网格，彩色网格可以分为[彩色顶点网格和彩色贴图网格](docs/color_mesh/color_mesh.ipynb)。


