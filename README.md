# KVS WebRTC example

# Descriptiopn / 説明

- This repo is an example for Amazon Kinesis Video Streams with WebRTC
  - based of https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-js
- これは Amazon Kinesis Video Streams with WebRTC のサンプルです

## KVS WebRTC について

- KVS WebRTC には、ルームに相当するシグナリングチャネル、ルームのオーナーに相当する Master、参加者に相当する Viewer がある
- 通信形態は2種をサポート
  - Master が1つ、Viewerが1つの1対1
  - Master が1つ、ViewerがNの1対N
  - いずれもViewerがOffer、MasterがAnswer
- Master-Viewer間の通信方向も双方向、片方向の両方が可能


# 使い方

## 準備

- AWS console の Kinesis Video Streams で 「シグナリングチャネル」を作成
  - シグナリングチャネル名を指定
  - 生成された ARN を確認
- AWS console の IAM でユーザーを作成
  - ユーザー名を指定
  - プログラムによるアクセスを許可（選択）
  - ユーザーグループを作り、AmazonKinesisVideoStreamsFullAccessポリシーを付与
  - 作成したユーザを、そのグループに追加
  - 生成されたアクセスキーID、シークレットアクセスキーを確認
- レポジトリをクローン
  - git clone https://github.com/mganeko/kvs_webrtc_example.git
- kvs_keys.js を編集
  - AWS_CHANNEL_ARN ... シグナリングチャネルのARNを指定
  - AWS_ACCESS_KEY_ID ... ユーザーのアクセスキーIDを指定
  - AWS_SECRET_ACCESS_KEY ... シークレットアクセスキーを指定
- ローカルのWebサーバーにhtml, jsファイルを配置

## ブラウザでアクセス


### 1対1の場合

- ブラウザで master.html を開く
  - Masterから映像/音声を送る場合は、[send video/audio]をチェック
  - [start master]をクリク
  - KVSと接続されるまで、20秒ぐらい待つ
- ブラウザで viewer.html を開く
  -  Viewerから映像/音声を送る場合は、[send video/audio]をチェック
  -  [start viewer]をクリック
  - KVSと接続されるまで、10秒ぐらい待つ
- P2P通信が確立して、相手の映像が表示される

### 1対nの場合

- ブラウザで master_multiviewer.html を開く
  - Masterから映像/音声を送る場合は、[send video/audio]をチェック
  - [start master]をクリク
  - KVSと接続されるまで、20秒ぐらい待つ
- ブラウザで viewer.html を開く（複数可能）
  -  Viewerから映像/音声を送る場合は、[send video/audio]をチェック
  -  [start viewer]をクリック
  - KVSと接続されるまで、10秒ぐらい待つ
- P2P通信が確立して、相手の映像が表示される


# License / ライセンス

* This sample is under the MIT license
* このレポジトリはMITランセンスで提供されます


