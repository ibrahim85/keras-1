# kerasで自動で分析を行うコード
- コマンドラインでデータセットのファイル名などと共に呼び出すことで、自動で分析を始めて完成したモデルを保存します。
- 保存したモデルを使って予測を行い、結果を別のファイルに出力します。
- 自動でバッチサイズ、エポック、ニューロン数、レイヤー数、ラーニングレートを変えてチューニングします。

## 準備するもの
- 1行目にヘッダーを付けたデータセット

　　・ CSV形式を推奨

　　・ 欠損値がある行は自動で除外されます

　　・ 外れ値は修正しておいてください

- auto_analyzer.pyとデータセットを同じディレクトリに設置
- 格納ディレクトリに書き込み権限を付与

## 使い方
1.コマンドラインを開く

2.データセットと本コードが格納されているディレクトリへ移動

3.「python auto_analyzer.py + パラメタ値」で呼び出す

### 呼び出し例
python auto_analyzer.py --mode create --input_file xxx.csv --method regression --model_file test --definition str,int,int

## パラメタ説明
### --mode（必須）
create：新しくモデルを作成する
predict：作ったモデルで予測する

### --input_file（必須）
データセットの入ったファイル名を入れる

### --method（必須）
binary：二値分類
multiple：多値分類
regression：回帰

### --output_file（非必須）
予測時に結果を格納するファイル名を入れる

### --model_file（非必須）
モデルを保存/読み込む際に参照

### --definition（非必須）
データ型が自動認識で問題がある場合に入力してください。
全カラム分のデータ型を[str, int, float]の中から選び、「,」カンマ区切りで入れてください。

## 動作環境
- python 3.5.0
- keras 2.0.3
