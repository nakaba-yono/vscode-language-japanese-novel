# Changelog

## 1.0.9

- 縦書きプレビューを複数のワークスペースで同時に実行できるようになりました。
    - 縦書きプレビューを実行したワークスペースは、8080から偶数番号ずつ増えるポート番号で縦書きサーバーを起動します。  
    外部のWebブラウザーや、モバイル端末から縦書きを表示するときは、8080、8082、8084と増えていく番号のいずれかを指定してください。


## 1.0.8

- 縦書きプレビューする言語を novel, plaintext, markdown の三種類に限定しました。

## 1.0.7

- [Issue ユーザー定義検索置換後に2桁の数字が含まれていると意図しない置換が発生する \#30](https://github.com/ttrace/vscode-language-japanese-novel/issues/30) by [nakaba-yono](https://github.com/nakaba-yono)に対処しました。

## 1.0.6

- アイコンをつけました。

## 1.0.5

- novel、markdown、plaintext以外の書類やウインドウを開いているときに文字数カウントを表示しないように修正しました。

## 1.0.4 debug release

- パッケージングのミスを修正しました。

## 1.0.3

- 1.0.0でマージした[Masayoshi Takahashi](https://github.com/takahashim)さんのPRを再度マージして、[Use fastest-levenshtein instead of (a copy of) levenshtein-edit-distance \#26](https://github.com/ttrace/vscode-language-japanese-novel/pull/26)をマージして、編集距離を用いるnpmモジュールを、[fastest-levenshtein](https://github.com/ka-weihe/fastest-levenshtein)に変更しました。
- 縦書きプレビューに自動縦中横機能をつけました。二桁の半角数字を縦中横でプレビューします。


## 1.0.2

- [Takahashi Masayoshi](https://github.com/takahashim)さんのPR、[Unify all settings of this extension with NovelSettings](https://github.com/ttrace/vscode-language-japanese-novel/pull/27)をマージしました
- 1.0.1 で書いた編集距離に関するワーニングを整理しました。

## 1.0.1

昨日以前のコミットがないときに編集距離が機能しない問題を解消しました。  
v1.0.1以降は、前日までのコミットが見つからない場合（作業当日の）最も古いコミットからの編集距離を表示します。

ステータスバーのアイコンを変更しました。

ファイルを開いたときに編集距離が更新されないバグを修正しました。

## 1.0.0

[Masayoshi Takahashi](https://github.com/takahashim)さんのPR、[Use fastest-levenshtein instead of (a copy of) levenshtein-edit-distance \#26](https://github.com/ttrace/vscode-language-japanese-novel/pull/26)をマージして、編集距離を用いるnpmモジュールを、[fastest-levenshtein](https://github.com/ka-weihe/fastest-levenshtein)に変更しました。

## 0.9.9

編集距離を算出する基準ファイルの更新日を、24時間前から、当日の0時に変更しました。
## 0.9.8

デバッグリリースです。  
catch-then構文を入れ変えました。大きなファイルを開いている時にレスポンスが悪くなっていた症状が軽減されます。


## 0.9.7

文字数表示欄に、前日からの編集距離を表示を搭載しました。  
前日の状態はGitのコミットを参照しているので、Gitで履歴管理されていないファイルの編集距離は表示できません。またファイル名をGit mvを用いずに変更した場合にも、編集距離の表示はできません。

編集距離には、最大0.5秒の遅延評価を行います。

編集距離は、MITライセンスで公開してくださっている[Titus Wormer](https://wooorm.com)さんの[levenshtein-edit-distance](https://www.npmjs.com/package/levenshtein-edit-distance)のソースコードを用いています。  
本来ならEMSモジュールをインポートして利用すべきところですが、Visual Studio Codeのエクステンションに組み込で利用する際の規則を私が理解していないため、ソースを直接埋め込んで利用させていただいています。

## 0.9.5

文字数のカウントに失敗するケースに対処しました。  
根本的な対策ではないので、近いうちに再実装しなおします。

## 0.9.3

全ドキュメントと締め切りフォルダーの文字数が、リアルタイム表示できるようになりました。  
標準ではないキーバインドを使っている場合には数字が反映されない場合があります。

## 0.9.2

Windowsでサーバーが404になるバグに対処しました。  
報告してくださった[Orito Itsuki](https://github.com/MatchaChoco010)さん、教えてくださった[開途](https://twitter.com/Kaito_YST)さん、ありがとうございます！
resolving a bug > [:bug: fix windows server path issue](https://github.com/ttrace/vscode-language-japanese-novel/pull/24) by [Orito Itsuki](https://github.com/MatchaChoco010)

## 0.9.1

文字数カウントのメニューを「締め切りフォルダー」に変更しました。  
また、締め切りフォルダーの設定時に目標の文字数を設定できるようになりました。

## 0.9.0

HTML形式のコメントアウトにもカラーリングを行うことにしました。

内部的な変更ですが、縦書きのプレビューだけを送信するhttpサーバーから、一般的なhttpサーバーに拡張しました。  
JavascriptやCSSを読み込むことができますので、今後の変更が楽になるかと思います。

HTMLにリセットCSSを導入しました。
(modern-css-reset)[https://github.com/andy-piccalilli/modern-css-reset]

## 0.8.4

フォルダーではなくテキストファイルを単独で開いたときに、機能拡張が動作しなくなってしまう問題を修正しました。
relolving: [textファイルを単独で開いたときにcommand not foundが出る](https://github.com/ttrace/vscode-language-japanese-novel/issues/22)

なお、テキストファイルを単独で開いた場合、原稿のコンパイルなどのコマンドは実行できません。

## 0.8.3

特定フォルダーの文字数をカウントできるようになりました。  
画面左のエクスプローラーでフォルダーを選択して［文字数カウント開始］を実行してください。  
長い小説の一部分や連載の文字数を計算する時に便利に使えるようになったと思います（必須でした！）

## 0.8.2

少数のフォントサイズが正しく設定できなかったバグを修正しています。  
おすすめの設定は、フォントサイズ2.5vhで40文字ですよ。

縦書きプレビューの更新時間を1.5秒よりも遅くならないように修正しました。  
長いテキストの場合にはもたつくかもしれませんが、後のバージョンでなんとかします。

## 0.8.1

ステータスバーでアクティブなドキュメントの文字数、プロジェクト全体の文字数を表示できるようになりました。  
プロジェクト全体の文字数は、ファイルを保存したタイミングで更新します。

なお、MITライセンスで公開されている8amjp/vsce-charactercountの成果を使わせていただいています。
[8amjp/vsce-charactercount](https://github.com/8amjp/vsce-charactercount)

## 0.8.0

テキストファイルの結合が可能になりました。
VS Codeで開いているフォルダー直下のテキストファイルを結合し、publishフォルダーの中に、フォルダー名のファイルを作ります。

VS Codeで開いているフォルダーの中に「原稿」あるいは「Draft」フォルダーがある場合には、そのフォルダーの中のテキストのみ結合します。

テキストを含むフォルダーが結合される時に、区切り文字を挿入できます。現在のバージョンは3文字落とした「＊」を挿入します。

## 0.7.6

[Masayoshi Takahashi](https://github.com/takahashim)さんの貢献によって、eslintを導入し、スクリプトの型安全性を見直しています。また、[Masayoshi Takahashi]さんには、 MITライセンスの記載方法も修正していただきました。

- [Define FontSize type as Template Literal Types](https://github.com/ttrace/vscode-language-japanese-novel/pull/4)
- [add eslint](https://github.com/ttrace/vscode-language-japanese-novel/pull/6)

プレビューのレスポンスを若干早めています。

## 0.7.5

0.7.4 で動作しなくなっていた縦書きのプレビューのバグを修正しました。

## 0.7.2

単独で開いたファイルも縦書きできるようになりました。

## 0.7.1

パッケージ依存の修正。utf-8-validateを入れ忘れていました。

## 0.7.0

このバージョンから、プレビューにnode httpサーバーを使い、テキストをwebsocketsで書き出すことにしました。  
今まではVisual Studio CodeのWebViewに直接HTMLを書き出していましたが、サーバーにしてプロセスを切り離すことで、以下のメリットが得られます。  

- テキストエディタのレスポンスを低下させずに、長いテキストをプレビューできる
- 他のコンピューターや、モバイルデバイスのブラウザーからプレビューを参照することができる
- 締め切りタイマーや進捗グラフなど、今後予定している機能追加が楽になる（jqueryを使い始めました）

また、サーバーだけ起動する\[Novel:プレビューサーバー起動\]メニューも追加しました。実行すると、縦書き表示に使っているlocalhost:8080で縦書きのプレビューサーバーが起動します。LANの他のコンピューターからも参照できますので、スマートフォンやタブレットなどをビュワーとしてお使いください。

また、このバージョンからエクステンションのスクリプトをjavascriptからtypescriptに変更しています。

## 0.6.9

プレビューのスクロール位置が追従しないバグの修正。

## 0.6.8

出力するPDFも、画面プレビュー時の行あたり字数を用いるように変更しました。

bug-fix:
ユーザー設定の正規表現検索置換の初期設定を修正。

## 0.6.4

青空文庫の字下げ注記に、簡易に対応しました。以下のように書くと縦書きのプレビューとPDF出力で3文字まで字下げすることが可能です。

```
［＃ここから３文字下げ］
字下げしたい段落。
［＃ここで字下げ終わり］
```

## 0.6.3

正規表現の検索置換ができなくなっていたのを修正。設定画面の例も修正。

## 0.6.1

会話の中に、サポートする括弧で囲まれた文があったとき、ハイライトするように修正。

HTML形式のコメントを、言語"novel"の blockcomment として定義した。コメントは、縦書きのプレビュー時に吹き出しで表示し、PDFを書き出す時には無視される。
