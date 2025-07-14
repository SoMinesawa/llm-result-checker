# LLM 実験結果チェッカー

LLM の実験結果を効率的にチェックするための Web アプリケーションです。

## 🚀 使用方法

### 1. セットアップ

```bash
# リポジトリをクローン
git clone https://github.com/SoMinesawa/llm-result-checker.git
cd llm-result-checker

# test.jsonを同じフォルダに配置
# (test.jsonがリポジトリに含まれている場合はスキップ)
```

### 2. 実行

```bash
# Webサーバーを起動（Python 3の場合）
python3 -m http.server 8000

# または Python 2の場合
python -m SimpleHTTPServer 8000

# またはNode.jsのhttpサーバー
npx http-server
```

ブラウザで `http://localhost:8000` を開き、`llm_checker.html` にアクセスしてください。

### 3. 使い方

1. **実験作成**: 新しい実験名を入力して「実験作成」ボタンをクリック
2. **実験選択**: 作成した実験をクリックして選択
3. **設定**:
   - シード値: ランダム順序を制御（デフォルト: 12345）
   - 開始位置: チェックを開始する位置（途中再開可能）
4. **チェック開始**: 「開始」ボタンをクリック
5. **評価**:
   - ✅ 正しい (C)
   - ❌ 間違い (W)
   - ⏭️ スキップ (S)
   - 🚪 終了 (Q)

## 🔧 機能

- ✅ **実験管理**: 複数の実験を作成・管理
- ✅ **自動保存**: 履歴を自動的にローカルストレージに保存
- ✅ **途中再開**: 前回の続きから再開可能
- ✅ **ランダム順序**: シード固定でランダムな順序でチェック
- ✅ **キーボードショートカット**: 効率的な操作
- ✅ **進捗表示**: 現在の進捗とオリジナルインデックスを表示
- ✅ **結果ダウンロード**: JSON 形式で結果を保存

## 📁 ファイル構成

```
llm-result-checker/
├── llm_checker.html     # メインアプリケーション
├── test.json           # 実験データ
└── README.md          # このファイル
```

## 💾 データ形式

### 入力データ (test.json)

```json
[
  {
    "object_ids": ["id1", "id2"],
    "conversations": [
      { "from": "human", "value": "質問" },
      { "from": "gpt", "value": "回答" }
    ],
    "object_captions": {
      "id1": "オブジェクト1の説明",
      "id2": "オブジェクト2の説明"
    },
    "metadata": {
      "sample_id": "sample_id_here"
    }
  }
]
```

### 出力データ (実験名\_results.json)

```json
{
  "experiment_name": "実験名",
  "checked_items": 100,
  "total_items": 6999,
  "shuffle_seed": 12345,
  "results": [
    {
      "index": 0,
      "originalIndex": 4531,
      "shuffledIndex": 0,
      "sample_id": "sample_id",
      "evaluation": "correct",
      "conversations": [...],
      "object_captions": {...},
      "timestamp": "2024-01-01T00:00:00.000Z"
    }
  ]
}
```

## 🔑 キーボードショートカット

- **C**: 正しい
- **W**: 間違い
- **S**: スキップ
- **Q**: 終了

## 🧪 実験管理

- 複数の実験を並行して管理可能
- 各実験の進捗は自動保存
- 実験の削除も可能
- 実験名と結果ファイルが対応

## 🌐 ブラウザ対応

- Chrome (推奨)
- Firefox
- Safari
- Edge

## 📝 注意事項

- `test.json` は必ず同じフォルダに配置してください
- データはブラウザのローカルストレージに保存されます
- 大きなファイルの場合、初期読み込みに時間がかかる場合があります

## 🐛 トラブルシューティング

### test.json が見つからない場合

- ファイルが同じフォルダにあることを確認
- Web サーバーが正常に起動していることを確認
- ブラウザのコンソールでエラーを確認

### 実験データが消えた場合

- ブラウザのローカルストレージが削除された可能性
- 同じブラウザ・同じドメインで使用してください

## �� ライセンス

MIT License
