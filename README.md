# groupByPrefix
共通の接頭辞を持つファイル(例: 連番画像ファイル)をフォルダにまとめるツールです

windowsシェルエクステンションを利用しているため、コンテクストメニュー(右クリックメニュー)に登録されます
* Windows 11の場合は「その他のオプションを表示」の中に登録されます ([参考](https://forest.watch.impress.co.jp/docs/serial/win11must/1363937.html))

## インストール方法
1. [Release](https://github.com/n-taka/groupByPrefix/releases/tag/v1.0)からzipアーカイブをダウンロード
2. zipアーカイブを適当な場所に展開
3. フォルダの中に入っている"install.bat"を**管理者として**実行

## アンインストール方法
1. フォルダの中に入っている"uninstall.bat"を**管理者として**実行
* groupByPrefix.dllを削除するだけでも、見かけ上はアンインストール出来ます。しかし、レジストリの一貫性が保たれなくなるため非推奨です

## 使い方
まとめたいファイルを選択後、右クリックメニューから"groupByPrefix"を選択してください

下記画像のように、それぞれの接頭辞ごとにフォルダが作成され、整理されます。

![how to use](https://github.com/n-taka/groupByPrefix/blob/main/doc/image_0.png)

* 上記画像では連番ですが、プログラムの動作としては、「連番であること」を**確認していません**
  * そのため、下記のような3ファイルを選択してgroupByPrefixした場合、同じフォルダ"aaa"にまとめられます
    * aaa123.jpeg
    * aaa456.png
    * aaa789.tiff
* 詳細なふるまいは以下のとおりになっています
  1. 拡張子を取り除いたファイル名が正規表現"\d+$"(末尾に1文字以上の数字)にマッチするかチェック
  2. 正規表現にマッチした場合、マッチした末尾の数字列を取り除く
  3. 残りの文字列を接頭辞とみなしてフォルダ作成
  4. 該当のファイルを作成したフォルダへ移動
  * 正規表現で末尾数字列を調べているため、"aaa001bbb002.jpeg"というようなファイル名の場合は"aaa001bbb"というフォルダが作られることになります

## 注意事項
* Windows 10の場合、アンインストール直後にgroupByPrefix.dllが削除できません (Windows explorerによって利用中というエラーが出ます)
  * 次回再起動以降、削除できるようになります
  * 再起動せずに、タスクマネージャー等を利用してWindows explorerを再起動しても削除できるようになります
  * Windows 11の場合は上記トラブルは発生しないようです

## 動作確認
* Windows 10 Pro (詳細なバージョン忘れました…)
* Windows 11 Pro (21H2)

## その他
[Microsoftのコードサンプル](https://github.com/microsoftarchive/msdn-code-gallery-microsoft/tree/master/OneCodeTeam/C%2B%2B%20Windows%20Shell%20context%20menu%20handler%20(CppShellExtContextMenuHandler))をベースにプログラムの作成を行いました。

## 連絡先
[@kazutaka_nakash](https://twitter.com/kazutaka_nakash)

## ライセンス
[MITライセンス](https://github.com/n-taka/groupByPrefix/blob/main/LICENSE)
