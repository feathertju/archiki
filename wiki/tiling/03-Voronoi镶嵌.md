---
tags:
  - tiling
  - tessellation
  - voronoi
aliases:
  - Voronoi Tessellation
  - Voronoi Diagram
  - Dirichlet Tessellation
---

# Voronoi 镶嵌

![[wiki/tiling/attachments/voronoi_tessellation.svg]]

## 基本原理

**Voronoi 图**（又称 Dirichlet 镶嵌）是将平面分割成若干区域的方法：每个区域包含一个**种子点**，该区域内任意一点到这颗种子点的距离都**小于到其他种子点的距离**。

- 不是"重复图案"，而是**根据点集生成的有机图案**
- 自然中广泛存在：肥皂泡、长颈鹿斑纹、龟裂、细胞组织结构
- 是**Delaunay 三角剖分**的对偶图

## 数学定义

给定平面上的 n 个种子点 $P = \{p_1, p_2, ..., p_n\}$，每个种子点 $p_i$ 的 Voronoi 区域为：

$V(p_i) = \{x \mid d(x, p_i) \leq d(x, p_j), \forall j \neq i\}$

## 适合镂空板的原因

| 特点 | 说明 |
|:---|:---|
| ✅ **完全参数化** | 调整种子点位置，每块板图案都不同 |
| ✅ **有机自然** | 没有重复感，适合现代/生物形态设计 |
| ✅ **Grasshopper 原生** | 有现成 Voronoi 运算器，无需额外插件 |
| ✅ **厚度渐变** | 可把单元面积映射为圆孔大小，实现渐变 |
| ⚠️ **需要控制** | 种子点太随机会产生极小单元，不利于加工 |

## 镂空板设计技巧

1. **边界约束**——用曲线约束种子点范围，避免图案超出边界
2. **最小孔距控制**——设置种子点之间最小距离，避免细薄部分断裂
3. **渐变密度**——调整局部种子点密度，形成疏密节奏
4. **圆角过渡**——Voronoi 单元顶点加圆角，增加强度

## Grasshopper 实现

```
Populate Geometry（生成随机点）→ Voronoi（生成多边形）
    → Offset（偏移为边框）→ Boundary（裁剪到边界）
```

## 参考

- [Wikipedia: Voronoi diagram](https://en.wikipedia.org/wiki/Voronoi_diagram)
- [Wolfram MathWorld: Voronoi Diagram](https://mathworld.wolfram.com/VoronoiDiagram.html)
