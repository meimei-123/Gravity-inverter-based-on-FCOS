# -该项目为基于FOC的三维重力异常反演。-
### 项目背景：重力异常是由于地下密度变化而引起的地表重力变化。简单的理解是，重力异常是能反映地下相对密度的heatmap，相对密度大的地方，重力异常高，相对密度小的地方，重力异常低。基于深度学习的三维重力异常反演问题就是使用深度神经网络来拟合ρ=f(g)中的f。
### 项目内容：使用FCOS作为反演网络，使用目标检测思路重新描述三维地下半空间的密度分布
### V1.0版本预计实现：
### ①生成1000个模型，每个模型空间由64*64*32个体素构成，每个空间中存在一个密度为1、均匀分布的长方体。长方体中心点所处位置随机。长方体体积有以下几类：1x1x1(100),2x2x2(100),4x4x4(200),6x6x6(200),8x8x8(400)。
### ②正演模型，生成输入数据；
### ③标签制作，对于一个模型来说，包含二分类分支标签、回归分支标签。其中分类分支标签为x*y*z = 64*64*32的矩阵，设空间中存在点(i,j,k)，若(i,j,k)在长方体内部，则ρ(x,y,z)=1，其余f(x,y,z)=0;回归分支为（z，ρ，x0，y0，x1,y1）,其中z表示所属深度层，ρ表示回归该深度上目标的密度，(x0,y0)表示西南角顶点坐标，（x1，y1）表示东北角顶点坐标。
