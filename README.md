このリポジトリに Container Visual Lab のMVPを構築してください。

まずREADME.mdを読み、MVP Goal / Scope / Out of Scopeを理解してください。
READMEに記載されていない機能を独断で追加しないでください。

## 技術スタック

以下を使用してください。

* React
* TypeScript
* Vite
* Three.js
* @react-three/fiber
* @react-three/drei
* Vitest
* npm

現時点では以下は使用しないでください。

* Next.js
* Tailwind CSS
* XState
* Redux
* Backend API
* Database
* Cloudflare Workers
* Docker Engineとの実接続

依存パッケージは必要最小限にしてください。

## MVPの初期ゴール

最初の実装では、3Dモデルの完成度よりアプリケーション構造を優先してください。

以下を実装してください。

1. React + TypeScript + Viteのプロジェクト構築
2. React Three Fiberによる3D Sceneの表示
3. Linux Kernelを表す簡単な3D土台
4. Whaleを表す仮の3Dオブジェクト
5. Web Containerを表す仮の3Dオブジェクト
6. 擬似ターミナルUI
7. 以下の状態遷移

NOT_BUILT
→ BUILT
→ RUNNING
→ STOPPED
→ REMOVED

8. 最低限、以下の擬似コマンドを認識する

docker build
docker run web
docker ps
docker stop web
docker rm web

コマンドは本物のDockerを実行せず、フロントエンド内部の状態のみ変更してください。

## 設計方針

3D表示、Dockerシミュレーション、UIを分離してください。

想定構造：

src/
components/
scene/
simulation/

3D Sceneのコンポーネント内にDockerコマンド判定ロジックを書かないでください。

simulation側で状態を管理し、scene側はその状態を受け取って表示を変更する構成にしてください。

## 3D Model

初期実装ではGLBファイルがなくても開発できるようにしてください。

最初はThree.jsのBoxGeometry等を利用した仮モデルで構いません。

将来的にBlockbenchで作成した以下のGLBへ差し替えられる構造にしてください。

public/models/whale.glb
public/models/web-container.glb

## UI

PCブラウザを第一対象とします。

画面は大きく、

* 3D Scene
* Terminal

の2領域に分けてください。

最初はデザインを作り込みすぎないでください。

## 品質

実装後は必ず、

npm run build

および利用可能なテストを実行してください。

TypeScriptの型エラーやビルドエラーを残さないでください。

最後に、

* 作成したもの
* ファイル構成
* 実装した状態遷移
* 実行方法
* 次に実装すべき内容

を簡潔に報告してください。
