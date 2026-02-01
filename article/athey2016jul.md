---
title: Recursive Partitioning for Heterogeneous Causal Effects
Tags:
Publisher: Proceedings of the National Academy of Sciences
DOI: https://doi.org/10.1073/pnas.1510489113
cite key: athey2016jul
description:
rating:
---
## Projects

zotero: [Full Text PDF](zotero://select/library/items/4FFE6T3I)
# Recursive Partitioning for Heterogeneous Causal Effects

## Authors
#auth/AtheyS #auth/ImbensG 

___
## ノート
%% begin notes %%
Write notes here!

%% end notes %%
___
## AI要約
___
提供されたソースに基づき、該当する論文の内容を「論文まとめフォーマット」に従ってまとめます。

---

#因果推論, #機械学習, #異質因果効果

### 1. どんなもの？

この論文は、実験研究や観察研究において、処置効果の異質性（Heterogeneous Causal Effects）を推定し、集団のサブセット間における処置効果の差の大きさを検定するための手法を提案しています。具体的には、**「因果木（Causal Trees）」と呼ばれるデータ駆動型のアプローチを用いて、処置効果が異なるサブグループへとデータを再帰的に分割します。

### 2. 先行研究と比べてどこがすごいの？

従来の機械学習手法（CARTなど）は、同じデ ータを使用してモデル構造の選択と推定の両方を行う「適応的（Adaptive）」な手法であり、過学習やバイアスが生じやすく、有効な信頼区間を構築することが困難でした。本論文の最大の特徴は、**「正直な（Honest）」推定**という概念を導入した点にあります。これにより、サンプルサイズに対して共変量が多い場合や、モデルの複雑さに制限を設けない場合でも、漸近的に正規分布に従う推定値と**有効な信頼区間を構築することが可能**になります。また、事前に分析計画（pre-analysis plan）でサブグループを指定しなくても、多重比較の問題を回避しながらデータから関連するサブグループを発見できる点も画期的です。

### 3. 技術や手法の"キモ"はどこにある？

- **正直な推定（Honest Estimation）:** トレーニングデータを、決定木の構造（分割ルール）を構築するためのサンプルと、その葉（リーフ）内での処置効果を推定するためのサンプルに分割します。
- **処置効果のための分割・交差検証基準:** 個人の処置効果は直接観測できない（因果推論の根本問題）ため、処置効果の平均二乗誤差（MSE）の不偏推定量を用いた新しい分割基準と交差検証基準を提案しています。
- **分散の考慮:** 分割基準において、より詳細な予測（小さいリーフ）による精度の向上と、サンプルサイズが小さくなることで生じる推定値の分散の増加とのトレードオフを明示的に組み込んでいます。

### 4. どうやって有効だと検証した？

3つの異なるデザインを用いたシミュレーション研究により、提案手法（CT-H: Causal Tree - Honest）と、従来の適応的手法（CT-A）、および他の手法（TOT: 変数変換、F: 適合度ベース、TS: t統計量ベース）を比較しました。

- **評価指標:** 真の処置効果が既知である前提での平均二乗誤差（Infeasible MSE）と、90%信頼区間の被覆率（Coverage rate）を評価しました。
- **結果:** 適応的な手法では信頼区間の被覆率が名目レートを大幅に下回ったのに対し、「正直な」手法はすべてのデザインで**名目通りの被覆率（約90%）を達成**しました。

### 5. 議論はあるか？

- **サンプル分割のコスト:** データを分割することで推定に使用できるサンプルサイズが減り、適合度（MSE）に一定の犠牲が生じる可能性があります。
- **観察研究への応用:** 強無視可能性（Unconfoundedness）の仮定の下で、傾向スコアを用いた重み付け（IPWなど）を組み合わせることで、観察データにも適用可能です。

### 6. 次に読むべき論文はあるか？

- 本手法をランダムフォレストに拡張した研究として、**Wager and Athey (2015)** "Estimation and Inference of Heterogeneous Treatment Effects using Random Forests" が挙げられます。
- 観察研究における傾向スコアの利用については、**Rosenbaum and Rubin (1983)** の基礎的な研究が参照されています。

### 論文情報・リンク

- [Susan Athey and Guido W. Imbens, "Recursive Partitioning for Heterogeneous Causal Effects," arXiv:1504.01132, 2015.](https://arxiv.org/pdf/1504.01132)
## 注釈


%% Import Date: 2026-01-25T21:46:54.477+09:00 %%
