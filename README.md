# Blender 3DGS / 4DGS Viewer Node | Blender 3DGS / 4DGS 可视化节点

![Banner Recommendation](asset/Banner_Corgi.png)


A custom Blender node developed by Mediastorm during the ASUS 4DGS Yungang Grottoes project. Supports loading and previewing of **3DGS** and **4DGS** datasets, with basic rendering styles for quick inspection.

由影视飓风团队在华硕 4DGS 云冈石窟项目中开发的 Blender 自定义节点，支持加载和预览 **3D Gaussian Splatting (3DGS)** 与 **4D Gaussian Splatting (4DGS)** 数据，并提供基础渲染样式以便快速查看与测试。

*4DGS素材下载: https://pan.baidu.com/s/1pYY0hi6xXo2q32mOzjXqJQ?pwd=ncdd

---

## 🧩 Features | 功能特点

- ✅ Load and visualize **3DGS** and **4DGS** `.ply` files
- ✅ Includes basic shader setups for stylized previews
- ✅ Designed to integrate into custom Blender pipelines
- 🧪 Experimental support for dynamic splatting with 4DGS
- ✅ 加载并可视化 `.ply` 格式的 **3DGS** 与 **4DGS** 数据
- ✅ 提供基础渲染样式节点，支持样式化预览
- ✅ 易于集成进自定义 Blender 渲染流程
- 🧪 初步支持 **4DGS** 时间动态点云的可视化探索

---

## 🔧 Requirements | 使用要求

- **Blender Version / Blender 版本**: 4.3 及以上
- **Platform / 平台**: Windows / Linux / macOS
- **Recommended GPU / 推荐显卡**: NVIDIA RTX 系列（更适配点云渲染）
- 建议使用4.5(Alpha)版本，尽管这是实验性版本，但可以获得更舒适的交互体验

---

## 🚀 How to Use | 使用方式
1. 克隆或下载本仓库
   
[![Preview](asset/M0.jpg)]()


3. 将资产添加进场景集合（如果是从网盘获取的工程，会自带一个柯基4Dply资产）
   
[![Preview](asset/M1.jpg)]()

3. 新建一个集合用于存放seq0~5，随后排除该集合
*由于一些限制，每个seq最多包含300帧（5秒）的时空
   
[![Preview](asset/M2.jpg)]()

5. 将节点组添加至场景中（如果你开启了一个全新的工程）
   
[![Preview]()]()

6. 使用节点读取包含 3DGS / 4DGS 数据的 `.ply` 文件，，按照图中设置
   
[![Preview](asset/M3.jpg)]()

6. Frame_Index_input参数指定了当前的时刻，你可以给他k关键帧，或者直接输入“#frame”指定一个驱动器
   
[![Preview](asset/M4.jpg)]()


> ⚠️ **Important Note / 注意事项**
> If your 4DGS `.ply` file contains an attribute named `t`, Blender will silently ignore it.
> Please **rename `t` to `ttt`** using an external tool.
> 
> 若你的 4DGS `.ply` 文件中包含属性 `t`，Blender 会因内部命名冲突忽略它。
> 请使用外部工具将 `t` 重命名为 `ttt`，由于 Blender 内部的命名解析机制存在特殊限制，原名为 t 的属性将无法正常识别，动画信息将无法加载。

---

## 🚀 Technology Exploration | 技术探索方向

As part of our ongoing R&D efforts in next-generation rendering pipelines, Mediastorm has been investigating Gaussian Splatting implementations within Blender's ecosystem. These technical explorations represent our commitment to pushing the boundaries of real-time visualization, though specific implementation plans remain flexible based on project requirements and partnership opportunities.

影视飓风团队始终致力于实时渲染技术的创新探索，我们在Blender生态内对高斯泼溅技术进行了前瞻性研究。这些技术方向体现了我们对图形学边界的持续探索，具体实施策略将根据项目需求和合作机会灵活调整。

### 🔍 Current Research Focus | 研究重点

We welcome academic and industrial collaboration in these areas:

我们欢迎学术界和产业界就以下方向展开合作：

#### 🔹 基于球谐函数的各向异性着色

*Each Gaussian point supports spherical harmonics (SH) based directional shading for natural soft lighting*

每个高斯点支持基于球谐函数（SH）的方向性着色，能还原更自然的柔性光照感。

#### 🔹 全空间高斯响应评估

*Gaussian response functions evaluated in complete 3D space*

高斯响应函数在完整 3D 空间中评估，确保空间一致性与物理合理性，使次级射线正确评估。

#### 🔹 实时渲染管线集成

[![Preview](asset/eevee_realtime_SH.gif)]()

*Eevee supports efficient Gaussian real-time preview for rapid debugging and visual development*

Eevee支持高效的Gaussian实时预览，便于快速调试与视觉开发。

#### 🔹 几何阴影交互

[![Preview](asset/eevee_realtime_shadow.gif)]()

*Gaussian points support shadow interactions (casting/receiving) with Mesh in both Eevee and Cycles*

高斯点与常规 Mesh 支持双向阴影投射与接收，已在 Eevee 与 Cycles 中实现。

#### 🔹 屏幕空间反射

[![Preview](asset/eevee_realtime_SSR.gif)]()

*Native Gaussian Screen Space Reflections implemented in Eevee for lightweight dynamic reflections*

在Eevee中实现了原生的高斯屏幕空间反射，可用于轻量级动点反射表现。

#### 🔹 路径追踪

[![Preview](asset/Path_tracing_4DGS.gif)]()

*Cycles supports Gaussian participation in ray-traced reflections*

Cycles支持高斯点参与光线追踪折射/反射，适配真实渲染需求。


---

## 🙏 Acknowledgements | 致谢

Special thanks to **Zhang Yu** from **4DV.ai**, who helped us understand the technical difference between 3DGS and 4DGS in the early stage of the project.

特别感谢来自 **视维智能 [4DV.ai](https://www.4dv.ai/zh)** 的 **张宇**，在项目初期耐心帮助我们梳理了 3DGS 与 4DGS 的底层原理，为节点工具的正确开发奠定了基础。
否则我们可能会一直以为 4DGS 只是多个 3DGS 串起来 :)

---

## 📺 Follow & Contact | 关注与联系

For updates and development logs (mostly in Chinese), visit:
如需了解更多开发动态与学习内容（中文更新）：
👉 [史莱姆的个人空间（Bilibili）](https://space.bilibili.com/383900492/)

---

## 📄 License | 许可协议

MIT License

MIT 开源协议
