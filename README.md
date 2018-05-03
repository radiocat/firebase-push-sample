# Firebaseを使ってプッシュ通知を試すサンプル

## 参考にしたサイト

https://www.mitsue.co.jp/knowledge/blog/frontend/201708/28_1146.html

## 実行手順

1. Forebase上にプロジェクトを作成し、コンソールから「ウェブアプリに Firebase を追加」

2. `env_sample.js` を `env.js` にリネームして `config` の内容を `env.js` にコピペする

``` bash
$ mv env_sample.js env.js
```

3. Firebaseにデプロイ（ローカルで試す場合は `firebase serve` ）

``` bash
$ firebase deploy
```

4. `index.html` にアクセスし、DevToolを開くとConsoleにトークンが出力されている

5. プッシュ通知の内容をFCMへPOST 


``` bash
$ curl --header "Authorization: key=<apiKey>" --header Content-Type:"application/json" https://fcm.googleapis.com/fcm/send -d "{\"registration_ids\":[\"<Consoleに出力されたトークン>\"], \"notification\":{\"title\":\"タイトル\",\"body\":\"プッシュ通知に表示される本文\"}, \"data\":{\"url\":\"URL\"}}"
```


