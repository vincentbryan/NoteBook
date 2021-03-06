## Matlab 简单问题

### 一、曲线插值与拟合

##### 1. 一维插值

e.g:

下表是待加工零件下轮廓线的一组数据，现需要得到x坐标每改变0.1时所对应的y的坐标

| x    | 0    | 3    | 5    | 7    | 9    | 11   | 12   | 13   | 14   | 15   |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| y    | 0    | 1.2  | 1.7  | 2.0  | 2.1  | 2.0  | 1.8  | 1.2  | 1.0  | 1.6  |

```matlab
x0 = [0, 3, 5, 7, 9, 11, 12, 13, 14, 15]
y0 = [0, 1.2, 1.7, 2.0, 2.1, 2.0, 1.8, 1.2, 1.0, 1.6]
x = 0:0.1:15
plot(x0, y0)

% 使用线性插值
y = interp1(x0, y0, x)
plot(x, y)

% 使用样条插值
y = spline(x0, y0, x)
plot(x, y)
```

##### 2.二维插值

e.g

在一个长为5个单位，宽为3个单位的金属薄片上测得15个点的温度值，试求出此薄片的温度分布，并绘出等温线图。（数据如下表）

|      | 1    | 2    | 3    | 4    | 5    |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 1    | 82   | 81   | 82   | 82   | 84   |
| 2    | 79   | 63   | 61   | 65   | 87   |
| 3    | 84   | 84   | 82   | 85   | 86   |

```matlab
temps=[82,81,80,82,84;79,63,61,65,87;84,84,82,85,86];
mesh(temps) 

width=1:5; depth=1:3; 
di=1:0.2:3; wi=1:0.2:5;

%增加了节点数目
[WI,DI]=meshgrid(wi,di);

%对数据（width,depth,temps）进行三阶插值拟合
ZI=interp2(width,depth,temps,WI,DI,'cubic'); 
surfc(WI,DI,ZI)
contour(WI,DI,ZI)

```

### 二、曲线拟合

e.g

弹簧在力F的作用下伸长x厘米。F和x在一定的范围内服从虎克定律。试根据下列数据确定弹性系数k,并给出不服从虎克定律时的近似公式：

| x    | 1    | 2    | 4    | 7    | 9    | 12   | 13   | 15   | 17   |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| F    | 1.5  | 3.9  | 6.6  | 11.7 | 15.6 | 18.8 | 19.6 | 20.6 | 21.1 |

```matlab
x=[1,2,4,7,9,12,13,15,17]; 
F=[1.5,3.9,6.6,11.7,15.6,18.8,19.6,20.6,21.1];
plot(x,F,'.')
% 从图像上我们发现:前5个数据应与直线拟合,后5个数据应与二次曲线拟合
a=polyfit(x(1:5),F(1:5),1);  
a=polyfit(x(5:9),F(5:9),2)
```

有时，面对一个实际问题，究竟是用插值还是用拟合不好确定，还需在实际中仔细区分

### 三、数值积分

e.g

现要根据瑞士地图计算其国土面积。于是对地图作如下的测量：以西东方向为横轴，以南北方向为纵轴。（选适当的点为原点）将国土最西到最东边界在x轴上的区间划取足够多的分点xi，在每个分点处可测出南北边界点的对应坐标y1 ，y2。用这样的方法得到下表

![图片1](img\图片1.jpg)

使用`trapz` 函数求轮廓的积分

### 四、数值微分

e.g

ß已知20世纪美国人口统计数据如下，根据数据计算人口增长率。（其实还可以对于后十年人口进行预测）

![图片2](img\图片2.jpg)

![图片3](img\图片3.jpg)

可以使用diff函数求解，也可使用数值差分公式求解

