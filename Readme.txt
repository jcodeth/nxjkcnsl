nxjkcnsl

■オリジナルからの変更内容など
NX-jikkyoのコメントを取得する非公式のコマンドラインツールです。

※呼び出し元プラグインの改造も必要です。
オリジナルのjkcnslとLコマンドの仕様が異なります。
例えばチャンネルjk1の場合、「Lch2646436」ではなく「L1」のようにチャンネルの
数値部分のみ渡してください。
コマンドの引数が異なるため、呼び出し元プラグインの改造も必要です。

現時点では下記の制限があります。
・コメント送信は未対応。（NX-jikkyoのWebサイトから送信してください。）
・nxjkcnslだけの問題ではありませんが、channelsUri指定での勢い情報は未対応。

■復旧までの一時利用を想定したNicoJK(xtne6f様版)の簡易的な改造例
NicoJK.cppの2168行目付近
 char ch[32];
 sprintf_s(ch, _countof(ch), "%d", currentJKToGet_);
 if (jkStream_.Send(hwnd, WMS_JK, 'L', ch)) {
 //if (jkStream_.Send(hwnd, WMS_JK, 'L', (it->chatStreamID + " " + cookie_).c_str())) {

JKStream.cppの87行目付近
 //_tcscat_s(jkcnslPath, TEXT("jkcnsl.exe"));
 _tcscat_s(jkcnslPath, TEXT("nxjkcnsl.exe"));


ライセンス等はオリジナルに従います。

以下、オリジナルのドキュメント

jkcnsl

■概要
おもにニコニコ実況のコメントを取得する非公式のコマンドラインツールです。

■使い方など
.NET Coreアプリなので(FrameworkでもビルドできますがClientWebSocketに決定的なバグ
があり使えません)、ビルドは各種のシェルでプロジェクトフォルダに移動し、
> dotnet publish -c Release -r win10-x86 /p:PublishSingleFile=true /p:PublishTrimmed=true
などとしてください。
動作環境はWindowsではWindows7以降と思います。
jkcnslを起動して、
> Lch???<改行> (←???は実況の番号)
などと打ち込めば、取得したコメントが流れます。終了は c<改行> や q<改行> と打ち込
んでください。

■ライセンス
MITとします。

■ソース
https://github.com/xtne6f/jkcnsl

■謝辞
実装にあたり特に https://github.com/tsukumijima/TVRemotePlus および
https://github.com/asannou/namami を参考にしました。とりわけ変数名など多くのアイ
デアをTVRemotePlusから借用しています。
