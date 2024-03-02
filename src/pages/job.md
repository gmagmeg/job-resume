---
title: job
layout: ../layouts/Layout.astro
---

# <i class="fa-regular fa-file-lines"></i>職務経歴書


<div class="toc">

<h2 class="top-h2">目次</h2>

- [経験領域](#経験領域)  
- [Sky株式会社での主な職務内容](#sky)  
  - [勤務管理システム](#kinmuhyou)
  - [出退勤打刻管理システム](#timecard)
  - [給与管理システム](#kyuyo)
- [GMOメイクショップ株式会社での主な職務内容](#GMO)
  - [外部連携決済の追加](#payment)
- [有限会社ビザンでの主な職務内容](#visan)
  - [ブラウザベースのペット美容室用POSレジ　保守開発](#pos)

</div>

### 個人データ

**氏名**：土田直人  

**職歴**：
<ul class="none">
  <li><span class="history-date">現在</span>Sky株式会社 在籍中</li>
  <li><span class="history-date">2019年7月</span>Sky株式会社 入社</li>
  <li><span class="history-date">2015年10月</span>GMOメイクショップ株式会社 入社</li>
  <li><span class="history-date">2015年7月</span>有限会社ビザン 退職</li>
  <li><span class="history-date">2012年6月</span>有限会社ビザン 入社</li>
  <li><span class="history-date">2012年5月</span>河北印刷株式会社 退職</li>
  <li><span class="history-date">2007年4月</span>河北印刷株式会社 入社</li>
</ul>

## <i class="fa-solid fa-code"></i>経験領域


- <span class="skill-title">開発・設計手法</span>アジャイル・スクラム開発、DDD、ウォーターフォール  
- <span class="skill-title">設計手法</span>DDD  
- <span class="skill-title">言語</span>PHP、JavaScript、TypeScript、Elm  
- <span class="skill-title">フレームワーク、ライブラリ等</span>Laravel、Vue.js、React、Next.js、Astor  
- <span class="skill-title">テストフレームワーク</span>PHPUnit、Jest  
- <span class="skill-title">DB</span>MySQL  
- <span class="skill-title">CI/CDツール</span>Jenkins、Gitlab CI

---

<h2 class="section-title"><i class="fa-regular fa-file-lines"></i>職務経歴詳細</h1>

<h2 id="sky"><i class="fa-solid fa-building"></i>Sky株式会社（2019年７月～現在に至る）</h2>

<h2 id="kinmuhyou" class="title top-h2">勤務管理システム</h2>

社員の月単位での勤務時間と、勤務内容をWebアプリ化するプロジェクト。  
既存のシステムを踏襲しつつ新規機能を拡充し、Excelで管理されている業務のシステム化を進めました。  

### <i class="fa-solid fa-users"></i>開発体制
9人（内訳：社員４名、パートナー２名、インターン生３名）  
短期間でのリリースを目的として、スクラムの要素を取り込んだ開発体制

### <i class="fa-solid fa-code"></i>主な使用技術
- バックエンドにLaravel（ver10）、フロントエンドにVue.js（ver2）を利用したSPA
- Dockerコンテナを用いたローカル開発環境の構築と利用
- GitLab CIを用いて、各種ドキュメント生成の自動化（WebAPIやコード、ER図など）
- PHPUnit, Playwrightを用いたユニットテストとe2eテストの導入、及び自動化
- Kibanaを用いてアクセスログからユーザー動向の把握

### <i class="fa-regular fa-flag"></i>プロジェクト内での役割
- 技術的に難しい部分の設計と実装
- 開発環境の整備と改善
- チームメンバーへの技術サポート
- コードレビュー
- ユニットテストのベース作成と自動化
- ドキュメントのベース作成と自動生成
- インフラ面の整備
- 利用者測定のためのデータ基盤整理


### <i class="fa-solid fa-person-running"></i>主な取り組み

<h4 class="top-h4">設計フェーズでDDDを導入</h4>

既存の業務フローがしっかり固まっており、業務ルールが複雑であること、
保守フェーズが続くことが明らかであったため、設計フェーズでDDDを用いることを決定しました。  
DDDを落とし込む際には、守らないといけない業務ルールをコードに落とし込むために、
用語の認識を合わせたいことを重点に話し、メンバーの納得を得たうえで導入しました。  
また継続するにあたり、用語やドメインモデル図をFigJamで管理し、メンバーが議論しながらメンテナンスしやすい土壌を整えました。  

#### 開発環境のDockerコンテナ化
既存の環境はVagrant+VirtualBoxで作られていましたが、起動が安定せず動作も重い、拡張しづらいなど様々な問題が多発し、開発者増員の妨げになっていました。  
そこでコンテナ環境へ移行することで既存の問題を解決し、開発者の増員に繋げました。  
またバックエンド、フロントエンド、Webサーバーでそれぞれコンテナを分離して管理する構成にしたため、
それぞれ開発用に拡張することが容易になり、開発効率を向上させました。  

#### デグレが多い機能へのPlaywrightによるe2eテストの導入
勤務表のExcelファイルアップロード機能について、複数の社内独自フォーマットが存在しており、とてもデグレに繋がりやすい機能となっていました。  
そこでフォーマットを網羅したe2eテストを導入し、誰が行っても同一の試験結果と期待が得られるようにし、デグレを減らすことに成功しました。  
またCIツールに組み込むことにより、万が一漏れがあった場合でもリリース直前には気づける仕組みづくりを行いました。  


<h2 id="timecard" class="title">出退勤打刻管理システム</h2>

出勤時間と退勤時間の管理をWebアプリ化するプロジェクト。  
社内と社外での切り分けや、認可者の自動選択部分をシステム化した。  

### <i class="fa-regular fa-flag"></i>プロジェクト内での役割

- k6、xdebugのprofiler、SlowQueryログ、Lighthouse負荷試験
- ドキュメントのベース作成と自動生成
- インフラ面の整備

### <i class="fa-solid fa-person-running"></i>主な取り組み

<h4 class="top-h4">SlowQueryの検証と改善</h4>

毎日使われるシステムであるためデータの増量が激しく、SlowQueryが日に1万件近く残るような状況でありました。  
そこでSlowQueryログを調査し、目立ったSQLを抽出しました。  
そしてデータ量が問題であることと、登録、更新が頻発するシステムであることを根拠に、
indexを貼ることよりも、データの取得量を減らす方向の修正案を開発者に提示し、修正をお願いしていきました。  
結果、SlowQueryログをバッチ処理以外では出力されないようになりました。  

#### 高負荷時の負荷検証とパフォーマンス改善

式典や社内のイベントごとで、2000リクエスト/秒のアクセスが発生する日があり、
このタイミングで最悪アプリが500エラーを返してしまう自体が発生しました。  
そこでk6を用いて負荷状況を再現し、どのアクセス量で500エラーが発生するのか、
エラーが起きているときにどのようなログが残っているのかを解析・原因の特定にあたりました。  
結果、SlowQueryが詰まってApacheの最大同時接続数（MaxKeepAliveRequests）を超えて、504エラーが発生してことが分かりました。  
その後SlowQueryを改善し、同じ状況を再現し、エラーが発生しないことを確認し、再発防止に努めました。  

<h2 id="kyuyo" class="title">給与管理システム</h2>

Excelで管理されていた給与や賞与に関するデータと計算をシステム化する

### <i class="fa-solid fa-users"></i>開発体制
2 ～ 4 人
内訳：社員２名、パートナー２名

### <i class="fa-solid fa-code"></i>主な使用技術
- バックエンドにLaravel（ver10）、フロントエンドにVue.js（ver2）を利用したSPA
- Dockerコンテナを用いたローカル開発環境の構築と利用
- PHPUnitを用いたユニットテストとe2eテストの導入、及び自動化
- Confluenceをベースに業務知識の展開

### <i class="fa-regular fa-flag"></i>プロジェクト内での役割

- 要件定義、設計、実装
- コードレビュー
- 開発環境の整備と改善
- ユニットテストのベース作成と自動化
- ドキュメントのベース作成と自動生成
- インフラ面の整備

### <i class="fa-solid fa-person-running"></i>主な取り組み

<h4 class="top-h4">実装でのリード</h4>

このプロジェクトは、部内で初めて採用されたLaravelとVue.jsを組み合わせた開発でした。  
プロジェクト立ち上げから、技術選定の理由や意思決定過程を明確に文書化し、
他のプロジェクトチームが参考にできるようにしました。  
この取り組みは、技術的な知見の共有を促進し、他プロジェクトからの技術的な質問や交流のきっかけとなりました。  
また、プロジェクトの進行とともに、システムの規模に合わせた構成変更や実装方針の見直しを行う柔軟性も身に付けました。  
実装当初は部内では新しい試みだった、Laravel + Vueのバックエンド・フロントエンドの構成でのプロジェクトの立ち上げになりました。  

#### 任意精度数値計算のデグレを防ぐためにユニットテストの導入
給与やそれにかかわる金額計算ということで、金額を扱う場面が非常に多く、
任意の桁数での切り上げ、切り捨てを間違えないで行うことが求められました。  
ここを間違えないこと、間違えたときにも気づきやすいようにユニットテストを導入し、デグレに気づけるようにしました。  
またCIに組み込むことでテストの実施漏れも無くしました。  

---

<h2 id="GMO"><i class="fa-solid fa-building"></i>GMOメイクショップ株式会社（2015年10月～2019年６月）</h2>

<h2 id="payment" class="title top-h2">外部連携決済の追加<br>　クロネコWebコレクト決済（クレジット・コンビニ・後払い）<br>　後払い.com決済、atone決済</h2>

### <i class="fa-solid fa-users"></i>開発体制
1～3人

### <i class="fa-solid fa-code"></i>主な使用技術
- PHP、jQuery、Git

### <i class="fa-regular fa-flag"></i>プロジェクト内での役割
- 設計、開発、保守
- 外部決済と既存システムの連携ドキュメント整理

### <i class="fa-solid fa-person-running"></i>主な取り組み

<h4 class="top-h4">決済共通処理の設計とモジュール化</h4>

決済に共通するコードのモジュール化に取り組み、外部APIとの通信や、文字コードの違いの吸収等、共通箇所を出来る限り関数化しました。  
最終的な結果として、1つの決済を導入するのに2,3ヶ月かかっている状況から、2週間まで短縮することに成功しました。  
また入力画面の多い決済画面の一部画面において、Seleniumによる一部動作テストを自動化し、デグレの低減とテスト工数を削減しました。  

---

<h2 id="visan"><i class="fa-solid fa-building"></i>有限会社ビザン（2012年６月～2015年７月）

<h2 id="pos" class="title top-h2">ブラウザベースのペット美容室用POSレジ　保守、開発</h2>

### <i class="fa-solid fa-users"></i>開発体制
1人

### <i class="fa-solid fa-code"></i>主な使用技術
- PHP5、jQuery

### 主な業務内容
- ブラウザベースのペット美容室用POSレジ　保守、開発、要件定義
- 顧客からの問い合わせに対するヘルプデスク、トラブル対応

### <i class="fa-solid fa-person-running"></i>主な取り組み

<h4 class="top-h4">レンダリング速度への配慮</h4>

WEBブラウザベースのPOSレジということで、レンダリング速度に特に気を付けました。  
実装時は仮想DOMといった考えもなく、描画の主だった部分をjQueryで賄っていましたので、何とかして描画速度を上げようと、
特に要素を絞り込みやすくするためのセレクタとHTMLコーティング、
使いまわせる要素はキャッシュするなど、できる範囲で気を配って実装しました。  
結果として描画速度については特に不満の声は上がりませんでした。  

---

<h2 class="company"><i class="fa-solid fa-building"></i>河北印刷株式会社（2007年４月～2012年５月）</h2>

### <i class="fa-regular fa-flag"></i>プロジェクト内での役割
Photoshop、illustratorを使用しての図形、写真の修正、MC-B2を使用した組版作業など、アナログな作業よりもデジタルな作業をメインに行っておりました。  
各種作業において自動化を図り、アクションやマクロの機能を積極的に使用しておりました。  

<a href="#" class="back-to-top">↑</a>