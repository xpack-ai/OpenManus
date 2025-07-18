# OpenManus \<> XPack

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) &ensp;

![Intro](./docs/assets/xpack/intro-bg.png)

[English](README.md) | [中文](README_zh.md) | [한국어](README_ko.md) | 日本語

## はじめに

このリポジトリは、**OpenManus** と **XPack.AI** の強力な統合を紹介し、世界中の数千の即座に使用可能なツールに接続することで、AIエージェントの機能を拡張する方法を実演しています。[OpenManus](https://github.com/FoundationAgents/OpenManus) の堅牢な基盤の上に構築されたこのプロジェクトは、XPackの広範なサービスマーケットプレイスを活用するためのモデルコンテキストプロトコル（MCP）サービスの設定の実用的な例を提供します。

## OpenManus とは？

[OpenManus](https://github.com/FoundationAgents/OpenManus) は、汎用AIエージェントを構築するためのオープンソースフレームワークです。異なる能力と動作を持つAIエージェントを作成するための柔軟なフレームワークを提供し、外部ツールやAPIへの簡単な接続を可能にし、完全にオープンソースでコミュニティ主導です。

## XPack.AI とは？

[XPack.AI](https://xpack.ai/) は、統一されたモデルコンテキストプロトコル（MCP）を通じて、AIエージェントがグローバルサービスとツールの広大なエコシステムに接続できるプラットフォームです。XPackを使用すると、AIエージェントの機能を簡単に拡張し、金融、物流、メッセージングなど、さまざまなドメインの多様なAPIやサービスに1分以内でアクセスできます。

## OpenManus + XPack：AIとグローバルサービスの橋渡し

このプロジェクトは、OpenManusをXPackをMCPサーバーとして利用するように設定する方法を実演することに焦点を当てています。これにより、OpenManusインスタンスはXPackの豊富なツールコレクションに即座にアクセスでき、以下のことが可能になります：

- **多様なサービスへのアクセス：** 金融データから画像処理まで、これまで手の届かなかった機能を統合します。
- **開発の加速：** 事前構築されたツールを活用して、AI駆動ソリューションを迅速にプロトタイプ化および構築します。
- **ワークフローの合理化：** OpenManusのインテリジェンスとXPackの外部サービス統合を組み合わせて複雑なタスクを自動化します。

## クイックスタート

### 1. OpenManus のインストール

まず、OpenManusがインストールされていることを確認してください。まだインストールしていない場合は、以下の[インストール](./docs/installation.md)セクションのインストール手順に従ってください。

### 2. XPack MCP の設定

OpenManusをXPackに接続するには、MCPサーバーを設定する必要があります。これにより、OpenManusはXPackを通じて利用可能なツールを発見し、利用できるようになります。

1.  **XPack認証キーの取得：**

    - [XPack.AI](https://xpack.ai/) にアクセスしてアカウントを登録してください。
    - XPackダッシュボードから認証キーを生成してください。

    ![XPack.ai Dashboard](./docs/assets/xpack/xpack-dashboard.png)

2.  **`mcp.json` の作成：**

    - OpenManusプロジェクトの `config` ディレクトリに、`mcp.json` という名前の新しいファイルを作成します。サンプルファイルをコピーして行うことができます：

    ```bash
    cp config/mcp.example.json config/mcp.json
    ```

3.  **`config/mcp.json` の編集：**

    - `config/mcp.json` ファイルを開き、XPack MCPサーバーの詳細を含むように変更します。**`YOUR_XPACK_AUTH_KEY`** を実際のXPack認証キーに置き換えてください：

    ```json
    {
      "mcpServers": {
        "xpack-mcp-market": {
          "type": "sse",
          "url": "https://api.xpack.ai/v1/mcp?apikey=YOUR_XPACK_AUTH_KEY"
        }
      }
    }
    ```

### 3. MCPでOpenManusを実行

設定が完了したら、MCPツール専用に設計された `main.py` スクリプトを使用してOpenManusを実行します。

```bash
python main.py
```

その後、ターミナルでアイデアやプロンプトを入力でき、OpenManusはXPackのツールを活用してタスクを実行します。

## 人気のタスク

このセクションでは、OpenManusとXPackをさまざまなタスクに活用する実用的な例を提供します。

### YouTubeコメントの分析と動画制作改善の提案

YouTube動画のコメントを簡単に分析して視聴者の感情を理解し、コンテンツ改善の提案を得ることができます。

```bash
python main.py
> Please use xpack-mcp-server to read the comments on this YouTube video: https://www.youtube.com/watch?v=LPZh9BOjkQs, analyze the sentiment of the feedback, and recommend improvements for the video.
```

![Analyze YouTube comments Image](./docs/assets/xpack/demo-youtube-analysis.png)

### 現在の金価格と影響要因

最新の金価格を素早く確認し、将来のトレンドに影響を与える可能性のある主要な要因を発見します。

```bash
python main.py
> Please use xpack-mcp-server to look up the current real-time price of gold and provide specific factors that may impact its price in the future.
```

![Current Gold Price Image](./docs/assets/xpack/demo-gold-monitor.png)

### 画像の背景除去

あらゆる画像の背景を瞬時に除去して、クリーンでプロフェッショナルな結果を得ることができます。

![remove bg origin image](./docs/assets/xpack/stunning-quality-product.png)

```bash
python main.py
> Please use xpack-mcp-server to remove the background from this image (https://oss.picturepicker.com/home/image/user/b60347f5-c984-4a09-a0aa-1ad6d2108056/0f1caf01-e3eb-449e-9d6d-d3d2276babc8/origin/20250708-cf563478ec5a4ffe9ced619ec62d733a-attachment.png) .
```

![A yellow handbag with the background removed](./docs/assets/xpack/demo-remove-bg.png)
