# 報酬に基づくブロック運搬動作の選択

ROS 2 Humble、Ignition Gazebo、Dockerを使ったブロック運搬の実験です。
指の閉じ角と手首の上昇量をCEMで探索し、初期設定と探索後の方策を比較します。
動作の順序は人が定めています。ニューラルネットや把持の教師データは使用していません。

実験の説明と再実行手順は [実験README](experiments/submission3/README.md) を参照してください。
レポートと動画は `experiments/submission3/report/` と `experiments/submission3/video/` にあります。

主なファイルは以下のとおりです。

- `compose.block.yaml`：固定Dockerイメージとワークスペース設定
- `tools/setup_reward_environment.sh`：環境確認とROSパッケージのビルド
- `ros2_workspace/training/reward_search.py`：探索と保存方策の評価
- `ros2_workspace/training/test_reward_search.py`：単体テスト
- `experiments/submission3/policies/`：比較に用いた保存方策
- `experiments/submission3/results/`：初回の探索履歴と評価記録
- `reproduction_evidence/`：新しいDocker環境での再実行記録

初回の比較は前後各3回で、どちらも全試行でゴールに到達しました。
平均の机上滑り距離は89.7mmから32.9mmへ減りましたが、滑りは残り、終端の位置誤差は増えました。
新しい環境でも運び方の違いは確認できましたが、数値の完全一致や未知配置への一般化は保証しません。

自作部分はApache-2.0です。第三者の利用条件は `THIRD_PARTY_BLOCK.md` を参照してください。
