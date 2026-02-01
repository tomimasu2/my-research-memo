---
title: "Uplift modeling with quasi-loss-functions"
Tags: 
Publisher: "Data Mining and Knowledge Discovery"
DOI: https://doi.org/10.1007/s10618-024-01042-x
cite key: hu2024jul
description:
rating: 
---
## Projects

zotero: [PDF](zotero://select/library/items/DZNRWWC5)
# Uplift modeling with quasi-loss-functions



___
## ノート
- モチベーション
	- 真のアップリフトを直接観測できない→アップリフトそのものを最適化する手法がない
		- meta-learner系
			- 予測誤差や傾向スコア誤差のみ
		- causal tree系
			- 介入群と対照群の分布の差を最大化するような分割基準を設計
			- 予測値と実績値との差を評価することは行なっていない
- 貢献
	- 真のアップリフトの不偏推定量となる疑似損失関数の定義（qusi-loss functions）
		- 擬似平均二乗誤差
		- 擬似平均絶対誤差
		- 擬似平均二乗誤差平方根
		- 擬似Huber損失
- Transformed Outcome
$$
Y_i^{*} = \frac{W_i}{e(X_i)}Y_i-\frac{1-W_i}{1-e(X_i)}Y_i
$$
			$W_i$  : 介入有無
			$Y_i$  : 観測されたアウトカム
			$e(X_i)$ : 傾向スコア（介入を受ける確率）
- 4つの損失関数
	- (1) Quasi Mean Squared Error (UpliftQL-MSE)

$$\hat{L}_{MSE}
= \frac{1}{N} \sum_{i=1}^N \left( \hat{\tau}(X_i) - Y_i^* \right)^2
$$
	- (2) Quasi Mean Absolute Error (UpliftQL-MAE)

$$\hat{L}_{MAE}
= \frac{1}{N} \sum_{i=1}^N \left| \hat{\tau}(X_i) - Y_i^* \right|
$$
	- (3) Quasi Root Mean Squared Error (UpliftQL-RMSE)

$$\hat{L}_{RMSE}
= \sqrt{
    \frac{1}{N} \sum_{i=1}^N \left( \hat{\tau}(X_i) - Y_i^* \right)^2
  }
$$
	- (4) Quasi Huber Loss (UpliftQL-HUBER)

$$\hat{L}_{Huber} =
\begin{cases}
\frac{1}{2} \left( Y_i^* - \hat{\tau}(X_i) \right)^2
& \text{if } \left| Y_i^* - \hat{\tau}(X_i) \right| \le \delta \\
\delta \left| Y_i^* - \hat{\tau}(X_i) \right|
- \frac{1}{2}\delta^2
& \text{otherwise}
\end{cases}$$

- 結果
	- 人工生成データ
		- バイナリ
			- トップ5にランクインしたモデルのうち、平均して**55%がUpliftQLモデル**
			- UpliftIVMもそこそこ強い
			- S-leanerやX-learnerは変換されたアウトカムに対しては誤差が小さい
		- 回帰
			- トップ5モデルのうち、平均して**32%がUpliftQLモデル**
			- 「介入群と対照群が無相関」のモードでは、個別に学習を行うメタラーナーの方が優れた結果となった
			- 傾向スコアに対して他のモデルよりもロバスト
- 今後
	- 新しい変換手法の導入
		- https://arxiv.org/pdf/1911.08729
	- 



___
## まとめるべきナレッジ
- GBDT, LightGBM, CatBoost
- Support Vector Machine

## 読むべき論文
- [Response Transformation and Profit Decomposition for Revenue Uplift Modeling](https://arxiv.org/pdf/1911.08729)

%% Import Date: 2026-02-01T11:13:54.629+09:00 %%
