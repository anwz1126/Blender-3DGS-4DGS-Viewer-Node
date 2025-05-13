# Blender 3DGS / 4DGS Viewer Node | Blender 3DGS / 4DGS 可视化节点

![Banner Recommendation](https://via.placeholder.com/1920x400/1a1a2e/ffffff?text=Blender+3DGS+4DGS+Viewer+Node+%257C+%E9%AB%98%E6%96%AF%E6%B3%BC%E6%BA%85%E5%8F%AF%E8%A7%86%E5%8C%96%E5%B7%A5%E5%85%B7)


A custom Blender node developed by Mediastorm during the ASUS 4DGS Yungang Grottoes project. Supports loading and previewing of **3DGS** and **4DGS** datasets, with basic rendering styles for quick inspection.

由影视飓风团队在华硕 4DGS 云冈石窟项目中开发的 Blender 自定义节点，支持加载和预览 **3D Gaussian Splatting (3DGS)** 与 **4D Gaussian Splatting (4DGS)** 数据，并提供基础渲染样式以便快速查看与测试。

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

---

## 🚀 How to Use | 使用方式

1. Clone or download this repository.
2. Open your project in **Blender 4.3+**.
3. Append the node setup into your file.
4. Use the node group to load `.ply` files containing 3DGS/4DGS data.
5. 克隆或下载本仓库
6. 使用 **Blender 4.3 及以上版本** 打开你的项目
7. 将节点组添加至场景中
8. 使用节点读取包含 3DGS / 4DGS 数据的 `.ply` 文件

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

[![Preview](https://via.placeholder.com/400x225?text=SH-based+Anisotropic+Shading)]()
*Each Gaussian point supports spherical harmonics (SH) based directional shading for natural soft lighting*
每个高斯点支持基于球谐函数（SH）的方向性着色，能还原更自然的柔性光照感

#### 🔹 全空间高斯响应评估

[![Preview](https://via.placeholder.com/400x225?text=3D+Gaussian+Evaluation)]()
*Gaussian response functions evaluated in complete 3D space*
高斯响应函数在完整 3D 空间中评估，确保空间一致性与物理合理性，避免透视失真。

#### 🔹 实时渲染管线集成

[![Preview](https://via.placeholder.com/400x225?text=Eevee+Realtime+Preview)]()
*Eevee supports efficient Gaussian real-time preview for rapid debugging and visual development*
Eevee支持高效的Gaussian实时预览，便于快速调试与视觉开发

#### 🔹 几何阴影交互

[![Preview](https://via.placeholder.com/400x225?text=Mesh+Shadow+Interaction)]()
*Gaussian points support shadow interactions (casting/receiving) with Mesh in both Eevee and Cycles*
高斯点与常规 Mesh 支持双向阴影投射与接收，已在 Eevee 与 Cycles 中实现。

#### 🔹 屏幕空间反射

[![Preview](https://via.placeholder.com/400x225?text=SSR+for+Gaussians)]()
*Native Gaussian Screen Space Reflections implemented in Eevee for lightweight dynamic reflections*
在Eevee中实现了原生的高斯屏幕空间反射，可用于轻量级动点反射表现

#### 🔹 光线追踪反射

[![Preview](https://via.placeholder.com/400x225?text=Ray-traced+Reflections)]()
*Cycles supports Gaussian participation in ray-traced reflections*
Cycles支持高斯点参与光线追踪反射，适配真实渲染需求


---

## 🙏 Acknowledgements | 致谢

Special thanks to **Zhang Yu** from **Visionwise AI**, who helped us understand the technical difference between 3DGS and 4DGS in the early stage of the project.

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
