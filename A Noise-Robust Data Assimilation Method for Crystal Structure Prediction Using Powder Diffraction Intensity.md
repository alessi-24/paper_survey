### A Noise-Robust Data Assimilation Method for Crystal Structure Prediction Using Powder Diffraction Intensity

> Seiji Yoshikawa, Ryuhei Sato, Ryosuke Akashi, Synge Todo, and Shinji Tsuneyuki

> The Journal of Chemical Physics

***
**補足**
- 理物の研究室
https://white.phys.s.u-tokyo.ac.jp/index2.php

***
**内容**
- 結晶構造の推定
- ポテンシャルエネルギーのグローバルミニマムを探したい
- 新たな結晶構造を生み出す方法
  - random sampling
  - genetic algorithm
  - paricular swarm optimization(PSO)
- ポテンシャル障壁を乗り越える方法
  - simulated annealing
  - basin hopping
  - minima hopping
  - metadynamics
- これらの手法はこれらの手法では数百の原始レベルしか扱えない。候補となる物質がシステムサイズの指数に比例して増加なので厳しい。
- モンテカルロとsimulated annealingで原子のポテンシャルとペナルティー関数をによるコスト関数で構造推定ができた
- ノイズに対するロバスト性が問題
- 新たなpenalty func.を導入

**実験データ同化**
- ベイズで考える
- penalty function : システム、全体的な構造を見ている(回折パターンのデータと計算データの差を反映)
- potential energy : 局所的な原子の相互作用を反映
- $\alpha$は penalty / potential の重み
- global minima が強調される
- potential を見るだけより最適化しやすい

**penalty 関数**
- 事前研究の$D_{cryst}$は対称性が低い or ピーク位置が決定しずらいときうまく働かない
- $D_{cc}$はピーク位置と強度にフィットできる
- 事前処理不要

**correlation coefficient penalty のシミュレーション結果**
- $D_{cryst}$ と $D_{cc}$ の精度を比較
- $\alpha$は penalty / potential の重み
- $\alpha$が0ではpotentialを重点化、$\alpha$が大きいほどpenalty(大域的な情報)を重点化
- $\alpha=20$ 程で$D_{cc}$を用いた場合では成功率1
- $D_{cryst}$を用いた場合では最高でも成功率0.5あたり
- $\alpha=0$付近(potentialのみを見ている)場合では、新たなpenalty指標でも成功率は0
- 大域的な情報を入れないとうまくいかない

*$D_{cc}$ : penalty指標とポテンシャルの関係を考察*
- penaltyを加えない場合
  - $D_{cc}$が0から1、つまり正解構造にfitしているものからしていないものまでポテンシャルの値が変わらない
  - 準安定、アモルファスになることを示唆
- correlation coefficient penaltyの場合
  - 正解構造にfitしていない構造はpotentialの値が大きく上昇
  - 滅多に得られない
- crystallinityの場合
 - 弱い制限しかかかっていない
- correlation coefficient penaltyの導入によって構造決定を加速化

**correlation coefficient penalty のノイズロバスト性**
- データに加えるノイズが大きくても構造推定できている
- ノイズに対するロバスト性もある

**感想**
- 何をもって成功としているのか？ピーク位置と強度情報？
- どの精度で成功としているのか？$10^{-2}$くらい？
- ノイズの大きさによって成功率が一番大きい$\alpha$の値が異なる。これは計算で導出できるのか？
- ノイズのロバスト性について考察しているが、他の手法ではどのくらいの成功率の変化なのかみたい
- $\alpha$に対する変化はないので、max成功率 vs 他の手法の成功率 で比較できそう