
|          | A          | B              | C           | D                |
| -------- | ---------- | -------------- | ----------- | ---------------- |
| 中文名      | 四月天        | 孔乙己            | 蜀道难         | 无衣               |
| 英文名      | april      | Kong           | road        | cloth            |
| Luogu 评级 | 普及/提高-     | 提高+/省选-        | 提高+/省选-     | NOI/NOI+/CTSC    |
| CF 评级    | 1400       | 2000           | 2000        | 3200             |
| 对标比赛     | CSP-J      | CSP-S          | NOIP        | 省选               |
| 分类       | 数学         | 动态规划           | 图论          | 数据结构             |
| 算法标签     | 证明         | 树形 DP          | Tarjan, BFS | 树套树, 欧拉函数        |
| 侧重点      | 思维         | 思维             | 算法+思维       | 算法+思维+模拟         |
| 题目来源     | EOlymp     | Revitalize, CF | CF          | Revitalize, BZOJ |
| 标准程序     | Revitalize | Revitalize     | Revitalize  | Revitalize       |
| 题解       | Revitalize | Revitalize     | Revitalize  | Revitalize       |
| 验题者      | Qaaxaap    | Qaaxaap        | Qaaxaap     | Qaaxaap          |

感谢参与 CWHOC 2026！  
如有疑问或建议，请洛谷私信出题人，请勿使用暴戾语言。  
如有意向投题于 CWHOC 2026 Day 2，非原创题请注明题目链接，原创题请标明题目描述、数据范围及题解。  
出题人洛谷账号链接：[Revitalize](https://luogu.com.cn/user/553192)

---
## A：四月天（april）
### About
出题人向若干 MO 省一大神询问本题做法正确性的证明后并未得到答复。  
### Hint 1
输入量极小，可以先尝试打表寻找规律，然后尝试证明。
### Hint 2
考虑表中质数情况及质数之次幂的规律。
### Hint 3
注意到原式关于 $n$ 是积性的。
## B：孔乙己（Kong）
### Hint 1
注意到整棵树最多在第【树高】时刻变为全 $0$，同时考虑每个节点的贡献。
### Hint 2
考虑树形 DP，并思考朴素做法，然后考虑优化。  
## C：蜀道难（road）
## D：无衣（cloth）
### Hint 1
考虑使用哪种数据结构维护欧拉函数，且可以运用其积性性质。
