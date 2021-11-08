# test_to_access_gdrive

コードを動かすためには、gdrive_access.py と同じ階層のフォルダ内に `settings.yaml`ファイルを作成する必要がある。<br>
yaml ファイルの内容は以下

```
client_config_backend: settings
client_config:
  client_id: *****your_client_id*****
  client_secret: *****your_client_secret*****

save_credentials: True
save_credentials_backend: file
save_credentials_file: credentials.json
get_refresh_token: True
oauth_scope:
  - https://www.googleapis.com/auth/drive.file
  - https://www.googleapis.com/auth/drive.install
```

GDrive に Python からアクセスするためには、いくつかの手順を踏む必要がある。<br>

1. https://console.developers.google.com/ この URL に入る。
1. 画面左にある「認証情報」をクリックして、画面上部にある「＋認証情報を作成」から「OAuth クライアント ID」を選択。
   1. 認証情報を作成するためには、次のいずれか 1 つの権限が必要だが現状ない。: serviceusage.apiKeys.create、clientauthconfig.clients.create、iam.serviceAccountKeys.create
1. アプリケーションの種類では、「テレビと入力が限られたデバイス」を選択（ここは、スクリプトからアクセスするために適当な選択肢がなかったのでこれを選択した。）
1. 適当な名前をつけて、作成する。
1. この際に表示される、「クラアンと ID」と「クライアントシークレット」は後ほど yaml ファイルを作成する際に必要になるのでメモしておく。
1. 次に、画面左側の「ダッシュボード」をクリックして、画面上部の「＋ API とサービスの有効化」をクリックする。
   1. ここでも有効化するためには権限が必要なのだが、現状ない。
1. 検索窓で、「Google Drive API」と検索して、Google Drive API が 1 番上に出るはずなので選択する。
1. ここで、API を有効にする。これで GDrive にアクセスするための準備は完了
