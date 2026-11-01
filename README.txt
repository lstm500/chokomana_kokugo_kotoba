ちょこまな ver.2（Streamlit + Supabase）

必要環境
Python 3.10以上。Streamlit Cloudでも実行できます。

配置するファイル
1. chocomana_app_ver.2.py → GitHubでは app.py に名前を変えて配置できます。
2. requirements.txt → 同じフォルダに配置。

初回設定
1. Supabaseプロジェクト kotoba_app に専用テーブル chocomana_state を作成済みです。
   同封の supabase_setup.sql は別プロジェクトへ移す場合の再現用です。
2. Streamlitのアプリ設定のSecretsに secrets.toml.example の内容を貼り付けます。
3. SUPABASE_SERVICE_ROLE_KEY に既存のservice_roleキーを設定します。
4. APP_PASSWORD に家庭で使うパスワードを設定します。
5. 起動時に家庭用パスワードを入力します。

ローカル実行
pip install -r requirements.txt
streamlit run chocomana_app_ver.2.py
ローカルの場合のSecretsは .streamlit/secrets.toml に設定します。

保存するもの
問題数・読み上げ・自動進行設定、直近1500回答（問題・選んだ答え・正誤・回答時間・ヒント使用・日時）、途中の問題。
同じCHOCOMANA_PROFILE_IDを使う端末間で共有します。
同時操作による上書き衝突は保存を停止して通知します。
保存失敗時は画面上部に未保存と表示し、再試行できます。
未保存のまま画面を閉じると、その分は引き継げません。
別のお子さんの記録を分ける場合は別のCHOCOMANA_PROFILE_IDを設定したアプリを用意します。
従来のSites版ブラウザ内の記録は自動移行しません。

学習内容
国語の反対語20問・仲間分け15問・短い説明15問。
短い説明は見本を読み、本人・保護者が確認します。AI採点・音声認識はありません。
その他の教科はメニューのみです。

確認済み
Pythonの保存・読込・更新競合・形式検証・設定不足表示・パスワード誤りのテスト。
実Supabase上での挿入・更新・読込・RLSとアクセス権（テストデータはロールバック）。
JavaScript構文検証。

未確認
実際の接続キーを設定したStreamlit公開環境での画面→DBの一連の動作。
スマホ実機と読み上げ音声。
この環境のプレビューはPythonランタイムに対応していないため、Streamlit版の画面確認は未実施です。
