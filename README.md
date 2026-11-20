# Mathematical Proofs in Lean 4 | 数学课题与形式化证明

Searchable index of mathematical problems, proof explanations, and Lean 4 formalizations by [yoaxi001](https://github.com/yoaxi001). Each entry states the scope of its formal verification.

本目录整理数学课题、证明说明和 Lean 4 形式化代码。请根据每项的证明范围判断结论，不把带有额外假设的形式化结果理解为无条件证明。

## Problems and proof status | 课题与证明状态

| Problem / 课题 | Repository / 代码与证明 | Formal verification scope / 形式化范围 |
| --- | --- | --- |
| Jian Liu’s Conjecture 5.1: triangle inequality for angle bisectors and medians / Jian Liu 猜想 5.1：三角形角平分线与中线不等式 | [triangle-bisector-median-inequality](https://github.com/yoaxi001/triangle-bisector-median-inequality) | Lean proof of the side-length formulation, including equality iff equilateral. / 边长公式表述及等号当且仅当等边三角形的形式化证明。 |
| Minimum sixth distance moment of centrally symmetric polygons / 中心对称多边形的距离六阶矩最小化 | [polygon-sixth-distance-moment](https://github.com/yoaxi001/polygon-sixth-distance-moment) | Conditional Lean proof from `PolygonDiskComparison`, including equality classification. / 在明确的圆盘比较假设下完成形式化推导及等号分类。 |

## Jian Liu’s Conjecture 5.1 — angle bisectors and medians

For a nondegenerate triangle with internal angle bisectors $w_a,w_b,w_c$, medians $m_a,m_b,m_c$, and semiperimeter $s$, the inequality is

$$
(w_a+w_b+w_c)(m_a^3+m_b^3+m_c^3)\ge s^4.
$$

Equality holds if and only if the triangle is equilateral.

- Source: Jian Liu, *Improvements of two inequalities in an acute triangle*, International Journal of Geometry 13 (2024), no. 4, 63–79, Conjecture 5.1, equation (5.2). [Original paper](https://ijgeometry.com/wp-content/uploads/2024/09/6.-63-79.pdf).
- Main theorem: `LiuMain.liu_conjecture_5_1` in [Main.lean](https://github.com/yoaxi001/triangle-bisector-median-inequality/blob/main/Main.lean).
- Equality theorem: `LiuEquality.equality_iff_equilateral` in [Equality.lean](https://github.com/yoaxi001/triangle-bisector-median-inequality/blob/main/Equality.lean).
- Scope: positive side lengths satisfying strict triangle inequalities; medians and angle bisectors are expressed using their standard formulas. The derivation of these formulas from a Euclidean point model is outside this formalization.
- 中文关键词：三角形不等式、角平分线、中线、半周长、等边三角形、Jian Liu 猜想 5.1、Lean 形式化证明。

## Centrally symmetric polygons — sixth distance moment

For fixed even $n\ge4$ and area one, the target result states that the regular $n$-gon minimizes the expected sixth power of the distance between two independent uniform points among centrally symmetric convex $n$-gons. Equality is characterized by translations and rotations of the regular polygon.

**Conditional formalization:** the Lean theorem takes `PolygonDiskComparison` as an explicit hypothesis. The project therefore formalizes the deduction from that geometric input, rather than an unconditional proof of every geometric ingredient.

- Main theorem: `SixthMoment.polygon_sixth_moment_with_equality` in [Equality.lean](https://github.com/yoaxi001/polygon-sixth-distance-moment/blob/main/Equality.lean).
- [中文证明说明](https://github.com/yoaxi001/polygon-sixth-distance-moment/blob/main/README.zh-CN.md).
- 中文关键词：中心对称凸多边形、正多边形、距离六阶矩、随机点距离、几何不等式、等号分类。

## Verification and attribution | 验证与说明

Both projects pin Lean and mathlib to v4.19.0. See each repository for build instructions, source files, and verification evidence. This index summarizes the repository documentation; updating the index does not itself rerun the proofs.

These projects were developed with AI assistance. Formal verification concerns the encoded statements and their explicit assumptions; it does not by itself establish novelty, publication priority, or independent expert review.

以上证明状态以各仓库所列的定理、假设和验证记录为准。新增课题时，请同时添加原始问题出处、证明文件、验证方式和未形式化的前提。
