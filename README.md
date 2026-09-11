# Attention Geometry Lab

用**几何视角**解释 Attention 的交互式教学网页：把 $QK^\top$、$\mathrm{softmax}$、$AV$ 这些矩阵运算，还原成"向量在空间里怎么转、怎么加权叠加"的可视化过程。

**在线访问 → <https://peterpanwasright-lab.github.io/attention-geometry/>**

## 页面

| 页面 | 主题 | 线上地址 |
| --- | --- | --- |
| `index.html` | 落地页，内嵌两个教程的实时预览 | [打开](https://peterpanwasright-lab.github.io/attention-geometry/) |
| `single-head.html` | 单头注意力几何：$Q,K,V$ 空间、注意力矩阵 $A$、$O=AV$ 的逐向量叠加 | [打开](https://peterpanwasright-lab.github.io/attention-geometry/single-head.html) |
| `multi-head.html` | 双头注意力几何：两个 head 的子空间对比、矩阵对比、多头输出合并 | [打开](https://peterpanwasright-lab.github.io/attention-geometry/multi-head.html) |

### 单头教程脉络

1. 输入序列与 token 表示
2. 原空间 $X$ → 投影到 $Q/K/V$ 三个子空间
3. 注意力矩阵 $A=\mathrm{softmax}\!\left(\frac{QK^\top}{\sqrt{d_k}}\right)$，含 causal mask 开关
4. V 空间中的输出 $O=AV$：单个输出向量是 V 的加权叠加
5. 首尾相接的叠加过程动画（几何直觉）
6. 一页总结：数学公式版 / 几何解释版 / 物理直觉版
7. 数值结果核对

### 双头教程脉络

1. 总体结构
2. 输入与参数
3. Head 1 与 Head 2 的几何空间对比
4. 两个 Attention Matrix 对比
5. 可切换 Head 的 $AV$ 向量叠加演示
6. 多头输出如何合并（concat → $W_O$）
7. 一页结论

## 设计取向

- **零外部依赖**：原生 JavaScript + Canvas 2D，无 CDN、无构建步骤，可离线打开；`.nojekyll` 关闭 Jekyll 处理。
- **可交互**：可编辑 token、$W_Q/W_K/W_V$、缩放系数 $a_z$，实时重绘几何与数值。
- **几何优先**：先看空间中的方向与长度，再看矩阵里的数字。

## 本地预览

```bash
git clone https://github.com/PeterPanWasRight-lab/attention-geometry.git
cd attention-geometry
python3 -m http.server 8000
# 打开 http://localhost:8000/
```

## 部署

仓库根目录即为站点根目录，通过 GitHub Pages 的 `main` 分支 / root 路径发布（Build type: legacy）。修改 `main` 分支后 Pages 会自动重新构建，无需 CI 工作流。

## License

MIT
