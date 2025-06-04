# マイクロサービスにおける認証方法と実装
## 2025/6/5
### Cognitoの検証
以下内容を実機（CognitoとAWS CLI）で検証した。  
https://dev.classmethod.jp/articles/get-started-with-amazon-cognito-now-1/
![image](https://github.com/user-attachments/assets/babe42a7-8303-4373-9173-c3c3af176612)

### EC2への接続の比較（ChatGPTに聞いただけ）
| 接続方式        | EC2 Instance Connect         | セッションマネージャー                | SSHクライアント                 | EC2シリアルコンソール                |
| ----------- | ---------------------------- | -------------------------- | ------------------------- | --------------------------- |
| **特徴**      | ブラウザ上から直接EC2に接続              | SSM Agent経由で接続、ログの記録・監査も可能 | 従来のSSH接続                  | OSレベルの起動トラブル時などに使う低レベルなアクセス |
| **利用条件・前提** | Amazon Linux/Ubuntu、IAM権限が必要 | SSM AgentとIAM権限が必要         | 鍵ペア、22番ポート開放、Elastic IPなど | Nitro EC2、IAMとVPC設定が必要      |
| **メリット**    | SSHキー不要、IAM制御可能              | VPC外から接続可能、セキュア、SSH不要      | 高速・柔軟、SSHツールが豊富           | OS障害時のトラブルシュートに最適           |
| **デメリット**   | 一部OSのみ対応、接続できない場合あり          | 初期設定が複雑、SSM Agentが必要       | 鍵管理が煩雑、セキュリティリスクあり        | CLIベース、日常利用には不向き            |


## 今後やりたいこと
以下イメージ図と案件でやろうとしていること（川畑さんに相談）して、案件のアーキ図を整理して実装（フィージビリティ担保）までやりたい。  
https://zenn.dev/rescuenow/articles/8396c8528a50e2
![image](https://github.com/user-attachments/assets/ad158e49-30c4-4244-8ff4-7e0582c18a5d)

