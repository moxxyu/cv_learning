# Learning Plan

## 一、学习方案概述与目标设定

**技能目标**：掌握工业视觉算法的核心理论知识和实践技能，能够独立完成工业缺陷检测、视觉定位、尺寸测量等典型任务。具体包括：

1. **理论基础**：精通数字图像处理、计算机视觉、机器学习等核心理论
2. **编程能力**：熟练使用 OpenCV、Halcon 等视觉库，掌握深度学习框架
3. **项目经验**：完成 3-5 个工业级视觉项目，具备从需求分析到系统部署的全流程能力
4. **硬件认知**：熟悉工业相机、镜头、光源等硬件选型和标定方法

## 二、第一阶段：理论基础学习（第 1-2 个月）

### 2.1 数学基础强化（每周 6 小时）

工业视觉算法的核心是数学，扎实的数学基础是理解和实现算法的前提。你已有规控算法背景，数学基础应该不错，但需要补充视觉相关的数学知识。

**线性代数**（重点）：

- 矩阵运算、特征值、奇异值分解（SVD）是图像处理的核心[(118)](https://blog.csdn.net/2301_77588508/article/details/145758809)
- 学习内容：向量空间、矩阵变换、仿射变换、投影变换
- 学习资源：《线性代数》同济版教材、3Blue1Brown 线性代数可视化课程
- 实践项目：实现 2D/3D 坐标变换、图像旋转缩放的矩阵表示

**概率与统计**：

- 贝叶斯定理、高斯分布、假设检验（用于模型评估）[(118)](https://blog.csdn.net/2301_77588508/article/details/145758809)
- 学习内容：概率分布、贝叶斯决策理论、最大似然估计
- 应用场景：图像噪声建模、分类器设计、异常检测

**微积分与优化**：

- 梯度、偏导数（理解神经网络的反向传播）[(118)](https://blog.csdn.net/2301_77588508/article/details/145758809)
- 学习内容：导数、梯度下降、凸优化、拉格朗日乘数法
- 应用场景：深度学习模型训练、参数优化

### 2.2 数字图像处理基础（每周 10 小时）

数字图像处理是工业视觉的基础，必须熟练掌握。建议采用 "理论学习 + OpenCV 实践" 的模式。

**图像处理基础理论**：

- 图像表示与操作：像素、通道、灰度图、RGB/HSV 色彩空间
- 图像增强与滤波：直方图均衡化、均值滤波、高斯滤波、中值滤波
- 边缘检测：Sobel、Canny 算子（结合梯度方向计算）
- 学习资源：冈萨雷斯《数字图像处理》第四版、OpenCV 官方文档

**OpenCV 实战训练**：

- 图像基本操作：裁剪、缩放、旋转、仿射变换
- 每天 1 小时练习：使用 OpenCV 实现各种图像处理算法
- 项目实践：

1. 图像去噪：对比不同滤波算法效果
2. 边缘检测：实现 Canny 边缘检测并优化参数
3. 图像分割：使用阈值分割和区域生长算法
4. 形态学操作：腐蚀、膨胀、开运算、闭运算

### 2.3 计算机视觉理论（每周 8 小时）

计算机视觉理论为后续的深度学习和工业应用奠定基础。

**传统计算机视觉**：

- 特征提取：Harris 角点检测、SIFT/SURF（尺度不变特征）、HOG（方向梯度直方图）
- 特征匹配：RANSAC 算法（消除误匹配）
- 相机模型：小孔成像原理、径向畸变、切向畸变
- 立体视觉：双目测距、视差计算、深度图生成

**深度学习基础**：

- CNN 架构：卷积层、池化层、全连接层的原理（如感受野、参数量计算）
- 经典模型：LeNet-5、ResNet（残差结构解决梯度消失）
- 目标检测：Two-stage（Faster R-CNN）、One-stage（SSD、YOLO）
- 图像分割：U-Net（医学图像分割）、Mask R-CNN（实例分割）

### 2.4 工业视觉系统认知（每周 4 小时）

了解工业视觉系统的组成和工作原理，为后续的硬件实践做准备。

**系统组成**：

- 工业相机：CCD/CMOS 传感器、分辨率、帧率、接口类型（GigE/USB3.0）[(65)](http://m.toutiao.com/group/7618473150468145706/?upstream_biz=doubao)
- 光学系统：镜头（焦距、光圈、景深）、光源（环形光、背光、同轴光）[(65)](http://m.toutiao.com/group/7618473150468145706/?upstream_biz=doubao)
- 图像处理单元：工控机、GPU 加速、算法软件

**系统选型**：

- 根据检测精度和视场计算相机分辨率[(56)](https://blog.csdn.net/Rocn666/article/details/148011287)
- 镜头焦距计算：f = (SensorSize × WD) / FOV[(56)](https://blog.csdn.net/Rocn666/article/details/148011287)
- 光源选择：根据被测物特性选择光源类型和颜色[(57)](https://blog.csdn.net/2302_76769566/article/details/151683714)

## 三、第二阶段：实践技能提升（第 3-4 个月）

### 3.1 工业相机与硬件实操（每周 8 小时）

充分利用可获得的工业相机、工控机等硬件设备，进行实际操作训练。

**工业相机操作**：

- 相机连接与参数设置：使用 Basler pylon 或海康威视 MVS 软件[(64)](http://m.toutiao.com/group/7619996007778107904/?upstream_biz=doubao)
- 相机标定：张正友标定法，使用 OpenCV 或 Halcon 完成[(68)](https://blog.csdn.net/xianzuzhicai/article/details/151876207)
- 图像采集：实现连续采集、触发采集、多相机同步
- 项目实践：

1. 使用工业相机采集不同光照条件下的图像
2. 标定相机内参和畸变参数
3. 实现图像的几何校正

**镜头与光源调试**：

- 镜头选型与安装：理解焦距、景深、工作距离的关系
- 光源配置：环形光、背光、同轴光的使用场景
- 打光实验：尝试不同光源角度和颜色，观察成像效果
- 项目实践：

1. 为特定工件设计照明方案
2. 优化光源参数以获得最佳对比度
3. 处理反光表面的打光技巧

### 3.2 视觉库与工具学习（每周 12 小时）

工业界常用的视觉库包括 OpenCV、Halcon、VisionPro 等，建议重点学习 OpenCV 和 Halcon。

**OpenCV 进阶**：

- 深度学习模块：使用 OpenCV DNN 模块进行模型推理
- 视频分析：光流法、目标跟踪、背景建模
- 3D 视觉：点云处理、立体匹配、相机标定
- 每天 2 小时练习：完成 OpenCV 官方教程的所有示例

**Halcon 入门**：

- Halcon 是工业界的标准软件，具有强大的算子库
- 学习内容：

1. Halcon 基本语法和数据类型
2. 图像预处理算子（滤波、增强、分割）
3. 几何形状匹配（find\_shape\_model）
4. 测量算子（measure\_pos、distance\_pp）

- 项目实践：使用 Halcon 实现一个完整的工业检测流程

**深度学习框架**：

- PyTorch：动态计算图、自定义模型、分布式训练
- 学习内容：

1. 张量操作和自动微分
2. 构建 CNN 模型
3. 数据集加载和数据增强
4. 模型训练和优化

- 项目实践：使用 PyTorch 实现简单的图像分类和目标检测

### 3.3 项目实战训练（每周 10 小时）

通过实际项目巩固所学知识，建议从简单到复杂逐步递进。

**初级项目（第 3 个月）**：

1. **基于 OpenCV 的工件检测**

- 功能：检测图像中的特定工件，输出位置和姿态
- 技术：边缘检测、轮廓分析、形状匹配
- 要求：检测准确率 > 95%，处理速度 < 100ms

1. **产品尺寸测量系统**

- 功能：测量工件的长度、宽度、角度等参数
- 技术：相机标定、透视校正、亚像素边缘检测
- 要求：测量精度达到 0.01mm

**中级项目（第 4 个月）**：

1. **基于深度学习的缺陷检测**

- 功能：检测 PCB 板或金属表面的缺陷
- 技术：YOLO 系列模型、数据增强、模型训练
- 要求：mAP\@0.5>0.95，推理速度 < 30ms

1. **多相机视觉定位系统**

- 功能：使用多个相机实现 3D 定位
- 技术：立体视觉、相机标定、手眼标定
- 要求：定位精度 < 0.1mm

## 四、第三阶段：专业方向深化（第 5-6 个月）

根据你的目标岗位（工业视觉缺陷检测、化工过程安全管控、列车智能运维、电力设备巡检），选择 2-3 个方向进行深入学习。

### 4.1 工业缺陷检测方向（每周 10 小时）

工业缺陷检测是最常见的应用场景，也是你的目标岗位之一。

**缺陷检测算法**：

- 传统方法：基于规则的缺陷检测（阈值、形态学）
- 深度学习方法：CNN、Transformer 在缺陷检测中的应用
- 无监督学习：使用异常检测算法处理少样本缺陷
- 学习资源：MVTec AD 数据集、YOLO 系列算法教程

**特定行业应用**：

1. **金属表面缺陷检测**（对应南钢需求）

- 常见缺陷：划痕、裂纹、孔洞、锈蚀
- 技术难点：表面反光、光照不均
- 解决方案：偏振光照明、多光谱成像、深度学习

1. **PCB 缺陷检测**（对应电子制造业需求）

- 常见缺陷：短路、断路、缺件、偏移
- 技术要求：高精度（0.01mm 级）、实时性
- 项目实践：使用 YOLOv12 实现 PCB 瑕疵识别[(83)](https://blog.51cto.com/u_13224944/14434885)

### 4.2 多模态视觉系统（每周 8 小时）

多模态融合是提高检测精度和可靠性的重要手段。

**红外视觉技术**：

- 红外热成像原理：热辐射、温度测量
- 应用场景：电气设备故障检测、化工管道泄漏检测
- 技术实现：红外相机标定、温度标定、图像处理

**多传感器融合**：

- 可见光 + 红外融合：提高复杂环境下的检测能力
- 2D+3D 融合：结合深度信息进行精确测量
- 多光谱成像：不同波长下的材料识别

**项目实践**：

1. 实现红外与可见光图像配准
2. 开发基于多模态的温度异常检测系统
3. 设计化工管道泄漏的视觉检测方案

### 4.3 智能运维与巡检（每周 8 小时）

针对列车智能运维和电力设备巡检需求，学习相关技术。

**运动目标检测与跟踪**：

- 背景建模：高斯混合模型、ViBe 算法
- 目标跟踪：卡尔曼滤波、粒子滤波、DeepSORT
- 轨迹分析：行为识别、异常检测

**巡检路径规划**：

- 基于视觉的导航：SLAM 技术、视觉里程计
- 路径规划算法：A\*、Dijkstra、RRT
- 避障算法：动态窗口法、人工势场法

**项目实践**：

1. 实现列车关键部件的自动检测
2. 开发电力设备巡检机器人的视觉系统
3. 设计基于视觉的轨道异物检测方案

## 五、第四阶段：项目综合开发（第 7 个月）

### 5.1 综合性工业视觉项目（每周 15 小时）

开发一个完整的工业视觉检测系统，涵盖从需求分析到系统部署的全流程。

**项目选择建议**：

1. **智能制造产线检测系统**

- 功能：检测产线上的产品缺陷、尺寸偏差、装配错误
- 技术架构：
  - 硬件：工业相机、光源、工控机
  - 软件：图像采集、算法处理、结果输出
  - 通信：与 PLC、MES 系统对接
- 开发流程：
  - 需求分析与方案设计（3 天）
  - 硬件选型与安装调试（5 天）
  - 算法开发与优化（10 天）
  - 系统集成与测试（7 天）

1. **智能工厂视觉监控系统**

- 功能：实时监控生产过程、检测异常行为、统计生产数据
- 技术特点：
  - 多相机协同工作
  - 实时视频流处理
  - 智能分析与预警

### 5.2 项目文档与代码规范（每周 5 小时）

工业项目要求严格的文档和规范的代码。

**项目文档编写**：

- 技术方案文档：系统架构、算法原理、实现方法
- 测试报告：功能测试、性能测试、可靠性测试
- 用户手册：系统操作、参数设置、故障排除
- 学习资源：IEEE 文档标准、公司内部文档模板

**代码规范与版本控制**：

- 使用 Git 进行版本控制，建立清晰的分支策略
- 遵循 PEP8（Python）和 Google C++ 风格指南
- 编写单元测试和集成测试
- 实现代码的模块化和可维护性

### 5.3 系统部署与优化（每周 5 小时）

将开发的算法部署到实际工业环境中。

**模型优化与部署**：

- 模型压缩：剪枝、量化、知识蒸馏
- 推理优化：使用 TensorRT、OpenVINO 等工具
- 部署平台：x86 架构、ARM 架构、GPU 加速

**工业环境适配**：

- 与 PLC 通信：使用 Modbus、OPC UA 协议
- 实时性要求：确保算法处理时间满足产线需求
- 可靠性设计：异常处理、自动恢复、日志记录

## 六、第五阶段：求职准备（第 8 个月）

### 6.1 简历优化与项目整理（每周 8 小时）

针对目标岗位（南钢、南化、中车浦镇、国电南瑞等）定制简历。

**简历撰写要点**：

- 突出工业背景：强调徐工研究总院的工作经验
- 项目经验：重点描述 3-5 个最相关的工业视觉项目
- 技能匹配：针对不同岗位调整技能描述的重点
- 量化成果：使用具体数据展示项目成果[(95)](http://test100a.100chui.com/article/485582.html)

**项目展示准备**：

- 整理项目代码，上传到 GitHub
- 制作项目演示视频，展示算法效果
- 准备项目报告，详细说明技术方案和实现过程
- 准备代码演示环境，能够现场展示关键算法

### 6.2 面试准备（每周 12 小时）

工业视觉工程师面试重点考察实践能力和问题解决能力。

**技术面试准备**：

1. **基础理论**：

- 数字图像处理基本概念（卷积、滤波、边缘检测）[(50)](https://blog.csdn.net/y2917526998/article/details/157216096)
- 相机标定原理和方法[(68)](https://blog.csdn.net/xianzuzhicai/article/details/151876207)
- 深度学习模型结构和训练方法

1. **算法实现**：

- 实现 Canny 边缘检测算法
- 编写简单的目标检测代码
- 解释 YOLO 算法的原理和优势

1. **项目经验**：

- 准备 2-3 个核心项目的详细介绍
- 使用 STAR 法则描述项目经历[(103)](https://www.nmgxhdn.com/news/jyxw/2025-09-05/12341.html)
- 准备应对 "项目中遇到的困难及解决方案" 类问题

**常见面试题**：

- 工业场景下如何处理光照不均的问题？
- 如何提高小缺陷的检测精度？
- 实时性要求下如何优化算法？
- 工业相机如何选型和标定？[(101)](https://www.iesdouyin.com/share/video/7555773978292276495/?region=\&mid=7555774010794036014\&u_code=0\&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ\&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ\&with_sec_did=1\&video_share_track_ver=\&titleType=title\&share_sign=kyVBYSdnlgDMQrUh1ZcoYMXmPKSQdpL10LO67RE2uVI-\&share_version=280700\&ts=1774362320\&from_aid=1128\&from_ssr=1\&share_track_info=%7B%22link_description_type%22%3A%22%22%7D)

### 6.3 目标企业调研（每周 5 小时）

深入了解目标企业的业务和技术需求。

**企业调研内容**：

1. **南钢**：了解钢铁生产流程、质量检测需求、技术发展方向
2. **南化**：了解化工生产特点、安全检测要求、自动化水平
3. **中车浦镇**：了解轨道交通装备制造、智能运维需求
4. **国电南瑞**：了解电力设备、智能电网、巡检系统

**岗位匹配分析**：

- 分析每个企业的技术栈要求
- 找出自己的优势和不足
- 准备针对性的面试策略

## 七、时间管理与学习计划

### 7.1 月度学习计划

| 月份    | 学习重点           | 理论学习  | 实践操作  | 项目开发  | 求职准备  |
| ----- | -------------- | ----- | ----- | ----- | ----- |
| 第 1 月 | 数学基础 + 图像处理    | 16 小时 | 8 小时  | 0 小时  | 0 小时  |
| 第 2 月 | 计算机视觉 + OpenCV | 16 小时 | 12 小时 | 4 小时  | 0 小时  |
| 第 3 月 | 工业相机 + Halcon  | 8 小时  | 16 小时 | 8 小时  | 0 小时  |
| 第 4 月 | 深度学习 + 项目实践    | 8 小时  | 12 小时 | 12 小时 | 0 小时  |
| 第 5 月 | 缺陷检测 + 多模态     | 8 小时  | 10 小时 | 10 小时 | 0 小时  |
| 第 6 月 | 智能运维 + 路径规划    | 8 小时  | 8 小时  | 12 小时 | 0 小时  |
| 第 7 月 | 综合项目开发         | 4 小时  | 8 小时  | 16 小时 | 2 小时  |
| 第 8 月 | 求职准备           | 0 小时  | 4 小时  | 8 小时  | 12 小时 |

### 7.2 周学习安排

**工作日（每天 4 小时）**：

- 早上：30 分钟 复习前一天内容
- 中午：1 小时 理论学习（在线课程）
- 晚上：2.5 小时 代码练习 + 项目开发

**周末（每天 8-10 小时）**：

- 上午：3 小时 理论学习
- 下午：4 小时 硬件实践 + 项目开发
- 晚上：2 小时 总结 + 计划

### 7.3 学习资源推荐

**教材与书籍**：

1. 《数字图像处理》（冈萨雷斯第四版）- 图像处理圣经
2. 《计算机视觉：算法与应用》- 实战导向
3. 《深度学习》（花书）- 深度学习理论基础

**在线课程**：

1. Coursera：Andrew Ng《Machine Learning》
2. Udacity：计算机视觉纳米学位
3. B 站：OpenCV 官方教程、Halcon 入门教程

**实战项目**：

1. GitHub：PaddlePaddle/awesome-DeepLearning[(76)](https://www.sohu.com/a/497251270_121124366)
2. Kaggle：工业缺陷检测竞赛
3. 工业数据集：MVTec AD、PCB 缺陷数据集

## 八、学习评估与调整机制

### 8.1 阶段性评估

为确保学习效果，建立以下评估机制：

**月度评估**：

1. 理论知识测试：每月末进行一次理论考试
2. 项目成果展示：展示本月完成的项目
3. 技能掌握评估：通过实际操作检验技能水平

**里程碑评估**：

1. 第 2 个月末：能够独立完成基础图像处理任务
2. 第 4 个月末：掌握工业相机操作和视觉库使用
3. 第 6 个月末：完成至少 2 个完整的工业视觉项目
4. 第 8 个月末：具备求职面试的全部能力

### 8.2 调整策略

根据评估结果及时调整学习计划：

**进度落后时**：

- 增加周末学习时间
- 简化部分项目要求
- 寻求在线指导或培训班

**进度超前时**：

- 增加项目复杂度
- 学习更多高级算法
- 提前开始求职准备

### 8.3 常见问题应对

**时间管理困难**：

- 制定详细的日程安排，严格执行
- 利用碎片时间复习知识点
- 减少娱乐活动，保证学习时间

**技术难题**：

- 建立学习笔记，记录问题和解决方案
- 加入技术论坛，寻求帮助
- 观看教学视频，理解原理

**实践机会不足**：

- 充分利用公司提供的硬件设备
- 寻找开源项目参与
- 购买或借用基础设备进行练习

## 九、成功转型的关键要素

### 9.1 学习方法建议

1. **理论与实践结合**：每个理论知识点都要通过代码实现来加深理解
2. **项目驱动学习**：通过实际项目串联知识点，提高学习效率
3. **持续总结反思**：定期总结学习心得，优化学习方法
4. **交流分享**：加入技术社群，与同行交流经验

### 9.2 心态调整

1. **保持耐心**：8 个月转型需要持续努力，不要期望一蹴而就
2. **勇于尝试**：遇到困难不要放弃，多尝试不同的解决方案
3. **注重积累**：每天进步一点点，积累起来就是巨大的飞跃
4. **保持信心**：相信自己的能力，坚持到底就是胜利

### 9.3 资源利用

1. **公司资源**：充分利用徐工研究总院的平台和设备
2. **网络资源**：善用 GitHub、Stack Overflow 等技术社区
3. **人脉资源**：与同事、朋友交流学习经验
4. **培训资源**：必要时参加专业培训课程

## 十、预期成果与发展展望

### 10.1 8 个月后达到的能力水平

经过 8 个月的系统学习，你将具备以下能力：

1. **技术能力**：

- 精通数字图像处理和计算机视觉理论
- 熟练使用 OpenCV、Halcon 等视觉库
- 掌握深度学习在工业视觉中的应用
- 能够独立完成工业视觉项目的全流程开发

1. **项目经验**：

- 完成 3-5 个工业级视觉项目
- 具备从需求分析到系统部署的完整经验
- 拥有可以展示的项目代码和成果

1. **求职竞争力**：

- 能够通过目标企业的技术面试
- 具备初级工业视觉算法工程师的任职资格
- 薪资期望可设定在 15-25K / 月

### 10.2 长期发展路径

成功转型后，你的职业发展路径可以规划为：

**1-2 年（初级工程师）**：

- 在目标企业积累工业视觉项目经验
- 深入了解特定行业的技术需求
- 提升算法优化和系统集成能力

**3-5 年（中级工程师）**：

- 能够独立负责复杂项目的技术方案设计
- 掌握前沿的视觉算法和技术
- 具备团队管理和技术指导能力
- 薪资可达 25-40K / 月

**5 年以上（高级工程师 / 技术专家）**：

- 成为行业内的技术专家
- 负责公司的技术创新和产品研发
- 可以考虑技术管理或创业路线

**参考资料**&#x20;

\[1] 【南京 工业视觉算法工程师招聘】-远景科技集团南京招聘信息-猎聘 <https://m.liepin.com/job/1980679473.shtml>

\[2] 【机器视觉算法工程师招聘】\_2025南京机器视觉算法工程师招聘信息-猎聘 <https://m.liepin.com/job/1974197765.shtml?pgRef=c_h5_city_search_page%3Ac_h5_city_search_job_listcard%402_74197765%3A1%3Agw.c5618f86-605108669>

\[3] 机器视觉算法工程师岗位核心职责与技能要求解析 <https://www.iesdouyin.com/share/note/7498184113237626122/?region=&mid=7482380548329982757&u_code=0&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&with_sec_did=1&video_share_track_ver=&titleType=title&schema_type=37&share_sign=kin8MGK5sWVrRPjORMR0GCrnUOqgZgM3accI7jzFxC8-&share_version=280700&ts=1774362271&from_aid=1128&from_ssr=1&share_track_info=%7B%22link_description_type%22%3A%22%22%7D>

\[4] 高级图像算法工程师(2025校招)职责\_南京鹏力科技集团2026年高级图像算法工程师(2025校招)岗位职责-BOSS直聘 <https://www.zhipin.com/job_detail/191b6e5927e6a0611Hx739m8GVdR.html>

\[5] 【南京 应用算法工程师招聘】-阿丘科技南京招聘信息-猎聘 <https://m.liepin.com/job/1978956509.shtml>

\[6] 职位详情 <https://m.quanzhi.com/job/detail/6929fdf6f9110e735a620b4c>

\[7] 「南京栖霞区 视觉算法工程师(工业自动化行业)招聘」\_2026年图漾科技招聘-智联招聘 <https://m.zhaopin.com/jobs/CC365767730J40784861307.htm>

\[8] 南京智能机器人公司视觉工程师工资待遇(招聘要求) - 职友集 <https://m.jobui.com/salary/nanjing-shijiaogongchengshi/ind-zhinengjiqiren/>

\[9] 工厂 职业 通关 指南 之 机器 视觉 工程师 # 工业 自动化 # 工厂 # 智能 制造 # 就业 # 培训 <https://www.iesdouyin.com/share/video/7615574325240253595/?region=&mid=7615574302292757254&u_code=0&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&with_sec_did=1&video_share_track_ver=&titleType=title&share_sign=c_.zNh2pxBWJxYZMLVdAOd5gixU7gHBn0jxoTIDSS0w-&share_version=280700&ts=1774362271&from_aid=1128&from_ssr=1&share_track_info=%7B%22link_description_type%22%3A%22%22%7D>

\[10] 【机器视觉工程师薪资待遇\_机器视觉工程师工资多少】-猎聘 <https://www.liepin.com/zpjiqishijuegongchengshi/xinzi/>

\[11] 视觉工程师 <https://m.qcc.com/jobdetail/daf45e43eb8d8eea3dec52667c320cb3.html>

\[12] 南京工业视觉行业发展现状和前景(工资待遇 | 人才需求 | 发展趋势) - 职友集 <https://m.jobui.com/salary/nanjing-all/ind-gongyeshijiao/>

\[13] 冠帝智能科技(南京)有限公司视觉工程师招聘信息 - 企查查 <https://m.qcc.com/jobdetail/f229a029b71f509c9c9d60f6cd668131.html>

\[14] 江苏工业机器视觉检测招聘网招聘信息 - 智联招聘 <https://m.zhaopin.com/zhaopin/962fc91be12a43808eafbbc49d03978a/>

\[15] 苏州昆山招聘图像识别算法工程师及机器视觉软件开发工程师 <https://www.iesdouyin.com/share/note/7267455634675649831/?region=&mid=7032687346218698789&u_code=0&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&with_sec_did=1&video_share_track_ver=&titleType=title&schema_type=37&share_sign=1.XO5fo3yO.ZJghHXmGpfkeCAM3H5NEDuoRr4sEPvJM-&share_version=280700&ts=1774362271&from_aid=1128&from_ssr=1&share_track_info=%7B%22link_description_type%22%3A%22%22%7D>

\[16] 机器视觉算法工程师-太仓人才网阳光版 <https://wap.tcrcsc.com/job.php?id=1096790>

\[17] 江苏省无锡市的Bosch的计算机视觉算法工程师\_BCSC职位 | Careerjet <https://www.careerjet.cn/jobad/cnfc989e1b7aa3de29e4c3a8ce8e9c324c>

\[18] 遨博(北京)智能科技股份有限公司招聘视觉算法工程师\_江苏校园招聘 <https://m.yingjiesheng.com/job-007-876-211.html>

\[19] 视觉算法工程师工作内容\_江苏润模汽车检测装备2026年视觉算法工程师工作要求-BOSS直聘 <https://activity.zhipin.com/job_detail/ad8fbf3e32c5e51e03J53N-1FFZU.html>

\[20] 「无锡新吴区 视觉项目开发工程师(J17179)招聘」\_2026年无锡先导智能装备股份有限公司招聘-智联招聘 <https://m.zhaopin.com/jobs/CC166275810J40866575703.htm>

\[21] 「南京浦口区 视觉应用工程师招聘」\_2026年南京华视智能科技股份有限公司招聘-智联招聘 <https://m.zhaopin.com/jobs/CC636566330J40646550206.htm>

\[22] 「机器人视觉算法工程师招聘」\_集萃智造招聘-BOSS直聘 <https://m.zhipin.com/job_detail/54211eaa08c7a24103Nz09m1FVdS.html>

\[23] 【南京 机器人视觉算法工程师招聘】-南京蔚蓝智能科技有限公司南京招聘信息-猎聘 <https://m.liepin.com/job/1976786073.shtml>

\[24] 南京奥特电气股份有限公司视觉工程师招聘信息 - 企查查 <https://m.qcc.com/jobdetail/daf45e43eb8d8eea3dec52667c320cb3.html>

\[25] 「机器视觉工程师招聘」\_南京美微智造科技招聘-BOSS直聘 <https://m.zhipin.com/job_detail/f7672ce2463dbcea03N53N28EVVT.html>

\[26] 安世智能科技(南京)有限公司高级视觉工程师招聘信息 - 企查查 <https://m.qcc.com/jobdetail/87e069b8d94d198b09e7504f4f8052c8.html>

\[27] 【南京 工业视觉算法工程师招聘】-远景科技集团南京招聘信息-猎聘 <https://m.liepin.com/job/1980679473.shtml>

\[28] 【算法工程师招聘】\_2026南京算法工程师招聘信息-猎聘 <https://m.liepin.com/job/1967092717.shtml>

\[29] 机器视觉算法工程师岗位核心职责与技能要求解析 <https://www.iesdouyin.com/share/note/7498184113237626122/?region=&mid=7482380548329982757&u_code=0&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&with_sec_did=1&video_share_track_ver=&titleType=title&schema_type=37&share_sign=kin8MGK5sWVrRPjORMR0GCrnUOqgZgM3accI7jzFxC8-&share_version=280700&ts=1774362282&from_aid=1128&from_ssr=1&share_track_info=%7B%22link_description_type%22%3A%22%22%7D>

\[30] 「图像算法工程师(南京)招聘」\_慧博云通招聘-BOSS直聘 <https://m.zhipin.com/job_detail/524e6a8c5d862a940nV63dS9ElpZ.html>

\[31] 「视觉算法工程师招聘」\_某大型自动化设备及智能制造公司招聘-BOSS直聘 <https://m.zhipin.com/job_detail/e3ffc74994274c0e03180tu5GVBU.html>

\[32] 「南京雨花台区 视觉工程师/图像学工程师招聘」\_2026年南京华群光电技术有限公司招聘-智联招聘 <https://m.zhaopin.com/jobs/CZ896695330J00193577806.htm>

\[33] 《机器视觉岗位职业技能等级规范》.pdf - 人人文库 <https://www.renrendoc.com/paper/457168879.html>

\[34] 「南京雨花台区 视觉硬件系统工程师招聘」\_2026年安徽行健智能制造装备股份有限公司招聘-智联招聘 <https://m.zhaopin.com/jobs/CCL1475964600J40874277212.htm>

\[35] 机器视觉调试工程师核心能力与学习路径解析 <https://www.iesdouyin.com/share/video/7485408801403817225/?region=&mid=7485408620381752118&u_code=0&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&with_sec_did=1&video_share_track_ver=&titleType=title&share_sign=bSw.mYlzozoK_MKFeuGLsuqtfI6xRPkHVt3onyFEoYo-&share_version=280700&ts=1774362282&from_aid=1128&from_ssr=1&share_track_info=%7B%22link_description_type%22%3A%22%22%7D>

\[36] 视觉工程师应届生需要掌握什么技能 - CSDN文库 <https://wenku.csdn.net/answer/3njv3g3twg>

\[37] 视觉工程师和助理机器视觉工程师有什么区别 - 职友集 <https://m.jobui.com/gangwei/pk/shijiaogongchengshi-zhulijiqishijiaogongchengshi/>

\[38] 《机械视觉工程师硬核技术分享:从算法到落地的全链路干货》-CSDN博客 <https://blog.csdn.net/lilinjun2003/article/details/158768750>

\[39] 机器视觉工程师需要掌握哪些核心技术?-朗观视觉 <https://m.langguan-vision.com/news/5266.html>

\[40] 人工智能机器视觉领域岗位需求与就业前景解析 <https://www.iesdouyin.com/share/note/7516443252452937018/?region=&mid=6952116110968163103&u_code=0&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&with_sec_did=1&video_share_track_ver=&titleType=title&schema_type=37&share_sign=KmSlT.K.Hch7DiD5VQ9kskVzREDkfIvvJKbRWUfmv7A-&share_version=280700&ts=1774362288&from_aid=1128&from_ssr=1&share_track_info=%7B%22link_description_type%22%3A%22%22%7D>

\[41] 机器视觉工程师的专长和特点 - CSDN文库 <https://wenku.csdn.net/answer/1pty708qtg>

\[42] 资深视觉算法工程师是什么职位\_温州市奕行智能装备2025年资深视觉算法工程师前景待遇-BOSS直聘 <https://m.zhipin.com/job_detail/7c33b53d1d5838f703By2t26F1VY.html>

\[43] 工业机器视觉现场工程师:在智能制造前线，他们凭什么成为「技术救火队员」?-CSDN博客 <https://blog.csdn.net/douyu0814/article/details/147693974>

\[44] 如何系统的进行机器视觉的学习\_机器视觉学习路线-CSDN博客 <https://blog.csdn.net/2301_77588508/article/details/145758809>

\[45] 机器视觉知识闭环的重要性与成为专业工程师的路径规划\_视觉工程师技术发展路线-CSDN博客 <https://blog.csdn.net/chenai886/article/details/135238783>

\[46] 从0学机器视觉:先学Python+OpenCV还是Halcon?高效学习路径解析\_外星眼机器视觉 <http://m.toutiao.com/group/7600257525867119131/?upstream_biz=doubao>

\[47] AI视觉工程师核心能力构建与系统学习路径解析 <https://www.iesdouyin.com/share/video/7568674357821320383/?region=&mid=7566024973884148480&u_code=0&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&with_sec_did=1&video_share_track_ver=&titleType=title&share_sign=v_jPrP798C9o3LUdNVwtN7hf0xZwh4CZkbe5QJhaHec-&share_version=280700&ts=1774362287&from_aid=1128&from_ssr=1&share_track_info=%7B%22link_description_type%22%3A%22%22%7D>

\[48] 从入门到精通:机器视觉系统的完整学习指南-朗观视觉 <https://m.langguan-vision.com/news/5959.html>

\[49] 工业视觉合集 工浦机器视觉+海康视觉 全流程课程+项目实战素材打包(55.81GB)\_系统 <https://m.sohu.com/a/967217741_122524051/>

\[50] 机器视觉工程师面试题总结(精简版)\_vision pro的脚本面试题-CSDN博客 <https://blog.csdn.net/y2917526998/article/details/157216096>

\[51] 目标检测算法应用工程师 面试高频题 + 标准答案\_目标检测面试题-CSDN博客 <https://blog.csdn.net/ZachLi/article/details/157478806>

\[52] C#与Halcon工业视觉开发高频面试题解析 <https://www.iesdouyin.com/share/note/7486774036958055743/?region=&mid=6537594780871265031&u_code=0&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&with_sec_did=1&video_share_track_ver=&titleType=title&schema_type=37&share_sign=xX6SZeSsJFqfHv1rXLlgKKCFTvlnM39TR.sKv39l9H0-&share_version=280700&ts=1774362288&from_aid=1128&from_ssr=1&share_track_info=%7B%22link_description_type%22%3A%22%22%7D>

\[53] 机器视觉工程师常见面试题及答案.docx-原创力文档 <https://m.book118.com/html/2025/1119/8002133125010011.shtm>

\[54] 机器视觉工程师面试题(某大型央企)精练试题详解.docx-原创力文档 <https://m.book118.com/html/2025/0917/5131202114012331.shtm>

\[55] 2025年工业AI计算机视觉试卷.docx - 人人文库 <https://www.renrendoc.com/paper/496200228.html>

\[56] 工业视觉系统选型全攻略:从相机、镜头到光源的参数解析与实战选型表\_工业相机产品需求表-CSDN博客 <https://blog.csdn.net/Rocn666/article/details/148011287>

\[57] 工业相机，镜头，光源的选型\_相机光源选型-CSDN博客 <https://blog.csdn.net/2302_76769566/article/details/151683714>

\[58] 工业机器视觉光源选择技巧与应用指南 <https://www.iesdouyin.com/share/video/7486406867443272970/?region=&mid=7486406711989783348&u_code=0&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&with_sec_did=1&video_share_track_ver=&titleType=title&share_sign=tzpJFnuElwHbYEOw36Bkb429G8ojsus5mVZqeVRkQSk-&share_version=280700&ts=1774362302&from_aid=1128&from_ssr=1&share_track_info=%7B%22link_description_type%22%3A%22%22%7D>

\[59] 在工业视觉任务中， 相机 镜头 光源的选型，应该是什么样的顺序 - CSDN文库 <https://wenku.csdn.net/answer/1dpjs3qd7p>

\[60] 工业相机光源怎么用?实操党真人拆解，避坑又好用 <https://www.do3think.com/encyclopedia/1004>

\[61] 工业机器视觉基础认知\_工控视觉是什么-CSDN博客 <https://blog.csdn.net/kylezhao2019/article/details/156477759>

\[62] 工业机器人视觉系统配置与调试完全指南:从硬件选型到实战应用\_视觉调试-CSDN博客 <https://blog.csdn.net/CHUXUEZHE8210/article/details/158925153>

\[63] 零基础机器视觉硬件环境快速搭建指南 <https://www.iesdouyin.com/share/video/7524586026904374555/?region=&mid=7524585956092005172&u_code=0&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&with_sec_did=1&video_share_track_ver=&titleType=title&share_sign=Y9FG.AeyJsb4xCBPQctICj2ViX6TyYbUkV1ZhnnBleY-&share_version=280700&ts=1774362302&from_aid=1128&from_ssr=1&share_track_info=%7B%22link_description_type%22%3A%22%22%7D>

\[64] 三步进阶!从“会用相机”到“能编程序”，筑牢工业视觉核心能力\_青华模具数控培训 <http://m.toutiao.com/group/7619996007778107904/?upstream_biz=doubao>

\[65] 机器视觉系统入门(Halcon/OpenCV)培训课程\_北京中科信软 <http://m.toutiao.com/group/7618473150468145706/?upstream_biz=doubao>

\[66] 单目相机标定完整流程 - 21ic电子网 <https://www.21ic.com/a/1001591.html>

\[67] 1月 8日 VM 视觉 检测 — 测量 项目 完整 版 # VM 视觉 检测 # halcon # 机器 视觉 检测 # 机器 视觉 培训 学习 # 自动化 设备 设计 @ 抖音 小 助手 @ 我 要 上 热门 <https://www.iesdouyin.com/share/video/7592912623377665322/?region=&mid=7592912839562054450&u_code=0&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&with_sec_did=1&video_share_track_ver=&titleType=title&share_sign=4gKCsg19QzcU0FoiqHwV29P.mr7MGYNLpnw4JredvRo-&share_version=280700&ts=1774362302&from_aid=1128&from_ssr=1&share_track_info=%7B%22link_description_type%22%3A%22%22%7D>

\[68] 相机标定(Camera Calibration)原理及步骤:从 “像素模糊” 到 “毫米精准” 的关键一步\_相机如何标定-CSDN博客 <https://blog.csdn.net/xianzuzhicai/article/details/151876207>

\[69] MATLAB相机标定工具箱实战应用详解-CSDN博客 <https://blog.csdn.net/weixin_42186015/article/details/153576782>

\[70] 内参工具 <https://docs.mech-mind.net/zh/eye-3d-camera/2.5.2/viewer/intrinsic-parameter-tool.html>

\[71] 内参工具 — Mech-Eye Industrial 3D Cameras 文档 <https://docs.mech-mind.net/latest/zh-CN/MechEye/MechEyeViewer/Tools/CheckCameraIntrinsicParameters/CheckCameraIntrinsicParameters.html>

\[72] 工业质检新标杆:YOLOv10缺陷检测案例-CSDN博客 <https://blog.csdn.net/gitblog_00098/article/details/151285577>

\[73] 工业视觉新范式:Kornia缺陷识别与微米级尺寸测量全流程实战-CSDN博客 <https://blog.csdn.net/gitblog_00670/article/details/152020284>

\[74] Intel® RealSense™ SDK:工业4.0应用案例解析-CSDN博客 <https://blog.csdn.net/gitblog_00426/article/details/151289154>

\[75] 10个实用的开源计算机视觉案例(含源码) PLC技术网-可编程控制器技术门户 <https://bbs.plcjs.com/thread-549680-1-1.html>

\[76] 代码全开源、一键运行的工业视觉检测案例教程，数据、算法、硬件全解析\_搜狐网 <https://www.sohu.com/a/497251270_121124366>

\[77] 【GitHub开源项目实战】Detectron2 全流程实战解析:面向工业级目标检测与实例分割任务的高性能开源平台-CSDN博客 <https://blog.csdn.net/sinat_28461591/article/details/147871715>

\[78] 完整机器视觉项目示例及相关资料，要免费的资料，资料要含源码 - CSDN文库 <https://wenku.csdn.net/answer/4sf4yksqma>

\[79] YOLOv12镜像实战应用:工业缺陷检测落地方案-CSDN博客 <https://blog.csdn.net/weixin_32836713/article/details/157495240>

\[80] YOLOv8实战案例分享:工业缺陷检测应用落地-CSDN博客 <https://blog.csdn.net/weixin_33173126/article/details/156467524>

\[81] YOLO12工业质检实战:缺陷检测与零件计数案例-CSDN博客 <https://blog.csdn.net/weixin_42113456/article/details/157952881>

\[82] 基于YOLO的焊缝缺陷智能检测与自动化返修系统 <https://www.iesdouyin.com/share/video/7582484799479139594/?region=&mid=7582484792126999336&u_code=0&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&with_sec_did=1&video_share_track_ver=&titleType=title&share_sign=iWDkBzzdnHwJax8F1kOXBA46U7rDFHXGeMzK06E1Pro-&share_version=280700&ts=1774362308&from_aid=1128&from_ssr=1&share_track_info=%7B%22link_description_type%22%3A%22%22%7D>

\[83] 从0到1搭建工业缺陷检测系统:基于YOLOv12的PCB瑕疵识别项目\_程序员威哥的技术博客\_51CTO博客 <https://blog.51cto.com/u_13224944/14434885>

\[84] 工业缺陷检测实战:用YOLOv10镜像快速定位瑕疵-CSDN博客 <https://blog.csdn.net/weixin_35748962/article/details/157576281>

\[85] 基于高分辨率特征图的工业产品表面缺陷检测算法\*(pdf) <http://www.giim.ac.cn/scipub/scipublist/y2025/P020250429358541173963.pdf>

\[86] 精心整理!2025年的30个CV计算机视觉项目推荐!-CSDN博客 <https://blog.csdn.net/easymcm/article/details/149863591>

\[87] 零基础学 AI:方向 1 计算机视觉(CV)核心任务与实战指南-CSDN博客 <https://blog.csdn.net/YongCheng_Liang/article/details/157843855>

\[88] 10个简单易学的AI计算机视觉开源项目，新手入门!\_计算视觉 入门开源项目-CSDN博客 <https://blog.csdn.net/Tecsae/article/details/105682475>

\[89] 25+ Exciting and Hands-On Computer Vision Project Ideas for Beginners to Explore in 2025 <https://www.upgrad.com/blog/computer-vision-project-ideas-for-beginners/>

\[90] Best Computer Vision Project Ideas for Beginners <https://www.placementpreparation.io/blog/computer-vision-project-ideas-for-beginners/>

\[91] 30 Computer Vision Projects for 2026 <https://www.analyticsvidhya.com/blog/2025/01/computer-vision-projects/>

\[92] Top Computer Vision Projects for Beginners in 2025 <https://www.guvi.in/blog/computer-vision-projects-for-beginners/>

\[93] 机器视觉工程师简历模板 | OpenCV图像处理 | AOI工业缺陷检测 <https://upcv.tech/jianlimoban/5390.html>

\[94] 机视觉算法工程师简历模板-猎聘 <https://www.liepin.com/mould/jsjsfgcs2d5r.shtml>

\[95] 图像算法工程师简历怎么写才能提高面试成功率-锤子简历 <http://test100a.100chui.com/article/485582.html>

\[96] 工科生技术岗位简历撰写核心要点与模板解析 <https://www.iesdouyin.com/share/video/7530968568592371003/?region=&mid=7530968480565578515&u_code=0&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&with_sec_did=1&video_share_track_ver=&titleType=title&share_sign=gXS56f9mVUWyuNAg_V5fL4oetjiZVMEB.B5_00NWn1U-&share_version=280700&ts=1774362320&from_aid=1128&from_ssr=1&share_track_info=%7B%22link_description_type%22%3A%22%22%7D>

\[97] 计算机视觉工程师简历-计算机视觉工程师简历模板在线制作 - 熊猫简历 <https://www.pandaresume.cn/jianli/17038.html>

\[98] 计算机视觉工程师简历模板 | AI工程师 | 深度学习 | CV <https://upcv.tech/jianlimoban/2314.html>

\[99] 面试机器视觉岗位的校招简历 - CSDN文库 <https://wenku.csdn.net/answer/6xwk9dpmp6>

\[100] 2025年机器视觉工程师岗位招聘面试题库及参考答案.docx-原创力文档 <https://m.book118.com/html/2025/1125/6111015211012015.shtm>

\[101] 机器视觉调试岗位面试核心问题与准备要点 <https://www.iesdouyin.com/share/video/7555773978292276495/?region=&mid=7555774010794036014&u_code=0&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&with_sec_did=1&video_share_track_ver=&titleType=title&share_sign=kyVBYSdnlgDMQrUh1ZcoYMXmPKSQdpL10LO67RE2uVI-&share_version=280700&ts=1774362320&from_aid=1128&from_ssr=1&share_track_info=%7B%22link_description_type%22%3A%22%22%7D>

\[102] 嘲风第七章:机器视觉面试技巧-周旋机器视觉工作室 <https://www.roundvision.cc/chaofengpdf/%E5%98%B2%E9%A3%8E%E7%AC%AC%E4%B8%83%E7%AB%A0%EF%BC%9A%E6%9C%BA%E5%99%A8%E8%A7%86%E8%A7%89%E9%9D%A2%E8%AF%95%E6%8A%80%E5%B7%A7/>

\[103] 面试通关指南:五步打造令人印象深刻的职场初印象 <https://www.nmgxhdn.com/news/jyxw/2025-09-05/12341.html>

\[104] 秋招面试应该注意哪些方面?避免 “无准备裸面”\_中华网 <https://3g.china.com/act/ent/11005281/20251020/48920079.html>

\[105] 企业员工招聘流程标准化模板.doc-原创力文档 <https://max.book118.com/html/2025/1126/6132215222012015.shtm>

\[106] 企业招聘流程标准化指南.doc-原创力文档 <https://m.book118.com/html/2026/0203/7163155045011050.shtm>

\[107] 工厂入职流程五步完成，面试当天安排宿舍 <https://www.iesdouyin.com/share/video/7548786653763915054/?region=&mid=7372966256951101475&u_code=0&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&with_sec_did=1&video_share_track_ver=&titleType=title&share_sign=YzkFbHqrcuaUjEK0YH3zBJFdo6uca82UvhG12v3leJg-&share_version=280700&ts=1774362320&from_aid=1128&from_ssr=1&share_track_info=%7B%22link_description_type%22%3A%22%22%7D>

\[108] 企业招聘流程标准化执行手册.doc - 人人文库 <https://www.renrendoc.com/paper/492615316.html>

\[109] 企业员工招聘流程手册版.pdf <https://m.book118.com/html/2026/0305/5204304003013131.shtm>

\[110] 国电南京自动化股份有限公司2026年校园招聘公告(第二批)\_国聘优选 <http://m.toutiao.com/group/7612189630007427584/?upstream_biz=doubao>

\[111] 数字图像处理总结(冈萨雷斯版)\_冈萨雷斯数字图像处理-CSDN博客 <https://blog.csdn.net/qq_43728886/article/details/122044373>

\[112] 冈萨雷斯《数字图像处理》读书笔记\_数字图像处理 读书笔记-CSDN博客 <https://blog.csdn.net/weixin_37625243/article/details/102556940>

\[113] 深度解析数字图像处理:冈萨雷斯课件中的7项重要理论 - CSDN文库 <https://wenku.csdn.net/column/27k1tnyyq4>

\[114] 《图像处理与机器学习》第六章图像增强技术解析 <https://www.iesdouyin.com/share/video/7493148682968255795/?region=&mid=7493148787016289059&u_code=0&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&with_sec_did=1&video_share_track_ver=&titleType=title&share_sign=d5FxKIgVXwCQOdjMbqOoKOq8CNn7aZ9Ee00vKM8OsNo-&share_version=280700&ts=1774362344&from_aid=1128&from_ssr=1&share_track_info=%7B%22link_description_type%22%3A%22%22%7D>

\[115] 冈萨雷斯《数字图像处理》学习指南:第四版全面解析(权威解读+实践技巧) - CSDN文库 <https://wenku.csdn.net/column/3ikvqohbu2>

\[116] 数字图像处理算法分析:冈萨雷斯课件实战指南的4大技巧 <https://wenku.csdn.net/column/7ydrwgiady>

\[117] 冈萨雷斯 数字图像处理各章内容总结总览\_数字图像处理(第四版)冈萨雷斯读书总结-CSDN博客 <https://blog.csdn.net/arthur_holmes/article/details/98608006>

\[118] 如何系统的进行机器视觉的学习\_机器视觉学习路线-CSDN博客 <https://blog.csdn.net/2301_77588508/article/details/145758809>

\[119] 图像处理-机器视觉算法中的数学基础-CSDN博客 <https://blog.csdn.net/JamesYu2022/article/details/158349223>

\[120] 机器视觉HALCON学习的数学基础要求解析 <https://www.iesdouyin.com/share/video/7488652517786520883/?region=&mid=7488652810444114751&u_code=0&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&with_sec_did=1&video_share_track_ver=&titleType=title&share_sign=jv2_ZNVUKg_Qae2XtkZ7s51GWf4UZtOrBa5k6mZRato-&share_version=280700&ts=1774362344&from_aid=1128&from_ssr=1&share_track_info=%7B%22link_description_type%22%3A%22%22%7D>

\[121] 刚入门机器视觉应该怎么规划学习路线?\_机器视觉学习路线-CSDN博客 <https://blog.csdn.net/cda2024/article/details/144851262>

\[122] 机器视觉入门需要掌握哪些知识点? <https://m.elecfans.com/zt/2089/javascript%20:history.back(-1)>

\[123] 应届生视觉算法工程师面试准备 - CSDN文库 <https://wenku.csdn.net/answer/5qt89uyho8>

\[124] 【计算机视觉】计算机视觉知识概览\_计算机视觉概览 视频-CSDN博客 <https://blog.csdn.net/weixin_43510208/article/details/148407619>

\[125] 详细介绍计算机视觉算法\_cv算法-CSDN博客 <https://blog.csdn.net/m0_66540684/article/details/145820305>

\[126] 2025年计算机视觉系统化学习路线解析 <https://www.iesdouyin.com/share/note/7529453414862867753/?region=&mid=6924223065245091841&u_code=0&did=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&iid=MS4wLjABAAAANwkJuWIRFOzg5uCpDRpMj4OX-QryoDgn-yYlXQnRwQQ&with_sec_did=1&video_share_track_ver=&titleType=title&schema_type=37&share_sign=wGwFQDcsVU.jZTGPvs68XWlE9WRxalqz_3d08J0B0IE-&share_version=280700&ts=1774362345&from_aid=1128&from_ssr=1&share_track_info=%7B%22link_description_type%22%3A%22%22%7D>

\[127] 计算机视觉基础原理与核心技术综述 - CSDN文库 <https://wenku.csdn.net/doc/237raz34u1>

\[128] 计算机视觉:原理、技术与未来展望-CSDN博客 <https://blog.csdn.net/cyjwukvuyxvunvuw/article/details/156126481>

