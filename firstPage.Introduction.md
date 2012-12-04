警告！DOM Enlightenmentの無料オンラインバージョンは最終バージョンでなく（初期リリース）初案である。この本の内容は事前編集そして事前記述編集の状態である。僕はこの本に文法的または技術的な間違いがあると思う。さらにこの本の内容は最新デスクトップブラウザ（IE9以上、Firefox最新、Chrome最新、Safari最新、Opera最新）が対象になっている。詳細な内容は紹介を読んでください。 

フィードバック　ぜひ、よろしくお願いします。フィードバックはメール(contact@codylindley.com)で頂くと嬉しい。この本は(編集、文法、技術的に足りない)初期バージョンである。僕は作品に対する技術的なフィードバックや論評に興味深い。ありがとう 


# DOM Enlightenment
#### JavaScriptと最新 HTML DOMとの関係について

By Cody Lindley Version: 0.2

翻訳：wanybae


## 紹介

この本は DOMスクリプディングや[JavaScript][1]の完璧な参考書ではない。でも、ライブラリ/フレームワークを使わずに DOMスクリプディングを行う際には一番完璧な本になると思う。この主題について著者が少ないのは理由がある。ほとんどの技術著者は古いブラウザとDOM 仕様の実装(もしくは足りない実装)の間に差があるからこの主題について語りたがらない。 

この本の目的のため(概念を共感するため)、僕はめっちゃくちゃなブラウザAPIを避けるし、現代的なDOM を漏出するための努力でブラウザ不一致をなくす。そう、僕はまさにこれにフォーカスして汚いものを避けよう。とりあえず、僕らはすべてのブラウザの醜さを扱うためjQueryのようなソリューションを持っている。もう消えてしまうブラウザを扱うさいにjQueryのようなものを使わなければならない。 

DOMスクリプディングのさいに必ずネイティブだけ使おうとするのではないけど、この本の一部では開発者がDOMスクリプディングのさいにDOMライブラリが必ず必要ではないのをわかるように書いた。さらに、単一環境(単一ブラウザ、モバイルブラウザまたはPhonegapのような HTML+CSS+JavaScript-to-native)のためJavaScriptコードを書く運よい誰かのために書いた。あなたがこの本をよんで学ぶものは理想的な状況、例えばWebKitモバイルブラウザのみで配信するために多少軽いDOMスクリプティングをするときならDOMライブラリを使わなずに実装ができることです。

### この本を読む読者に
僕は二つタイプの開発者を考えながらこの本を著述した。この二つのタイプ共すべてJavaScript, HTML, CSSについて中級から高級のスキルを持っていたと仮定した。一つ目のタイプはJavaScriptやjQueryはうまく使えるがjQueryのようなライブラリの目的と価値を(知りたいが運が合わなくて)理解するほどの時間を持っていなかった開発者だ。この本から得る知識でこんな開発者はDOMスクリプティングのためにjQueryで提供している価値を完璧に理解することになると思う。そして価値だけじゃなくてjQueryがどうやってDOMを抽象化しているか、どこからなんでjQueryがこの差を埋めているのかを理解できると思う。二つ目のタイプはひたすら最新ブラウザで動作するか多数のOSと機器のためネイティブコードに変換される(Phonegap) HTMLドキュメントをスクリプティングする作業を行ってライブラリのオーバーヘッド(大きさもしくは大きさ対使用性)を避ける必要があるエンジニアだ。 

### 技術的な意図、勘案、制限
* この本に含まれている内容とコードは最新ブラウザ(IE9以上、Firefox最新、Chrome最新、Safari最新、Opera最新)を考えて作成した。僕の目標は最新ブラウザのネイティブに当たる概念とコードのみを含むことだ。もし僕がこんな目標から外れることになると読者にこんなことを知らすことになる。だいたい特定のブラウザが持つもしくは少数の最新ブラウザだけが実装したものもこの本に書かないようにした。
* この本で特定のDOM、CSS、HTML明細書を独断の観点で見なかった。ここで特定の仕様を独断で代弁するのは僕が望むものではない。これは現在進行中の仕様を数えることとブラウザが仕様通りに実装しているかヒストリと現状を確認することになるのでとても大きな作業(価値のないことだと思う)になっちゃう。僕はいくつの仕様([Document Object Model (DOM) Level 3 Core Specification][2], [DOM4][3], [Document Object Model HTML][4] ,[Element Traversal Specification][5], [Selectors API Level 2][6], [DOM Parsing and Serialization][7], [HTML 5 Reference][8], [HTML 5 - A vocabulary and associated APIs for HTML and XHTML][9], [HTML Living Standard][10], [HTML 5 - A technical specification for Web Developers][11], [DOM Living Standard][12])の内容を主観的に活用してバランスを合わせた。この本の内容はコミュニティーなどに基盤をおいていて特定のスペックを独断で表現しようとしなかった。
* DOMだけじゃなくて様々な主題を対象にした。読者がCSSとJavaScriptをつなげてDOMを適切に理解できるようにこんな主題を含んだ。
* わざとXMLやXHTMLについては書かなかった。
* 本のボリュームを減らすためform,table APIも書かなかった。でも、今後このセクションを追加するかもしれない。

### ライセンス
DOM Enlightenment HTMLバージョンは[クリエイティブコモンズ著作者表示-非営利-変更禁止3.0][13] Unportedライセンスでリリースされた。			

### ハードコピー＆ebook
[O'Reilly][14]からハードコピーとebookを発刊して販売する予定


[1]: http://javascriptenlightenment.com/ "JavaScript Enlightenment"
[2]: http://www.w3.org/TR/2004/REC-DOM-Level-3-Core-20040407/core.html "Document Object Model (DOM) Level 3 Core Specification"
[3]: http://www.w3.org/TR/dom/ "DOM4"
[4]: http://www.w3.org/TR/2003/REC-DOM-Level-2-HTML-20030109/html.html "Document Object Model HTML"
[5]: http://www.w3.org/TR/ElementTraversal/ "Element Traversal Specification"
[6]: http://www.w3.org/TR/selectors-api2/ "Selectors API Level 2"
[7]: http://domparsing.spec.whatwg.org/ "DOM parding and Serialization"
[8]: http://dev.w3.org/html5/html-author/ "HTML 5 Reference"
[9]: http://www.w3.org/TR/html5/ "A vocabulary and associated APIs for HTML and XHTML"
[10]: http://www.whatwg.org/specs/web-apps/current-work/multipage/ "HTML Living Standard"
[11]: http://developers.whatwg.org/ "HTML 5 - A technical specification for Web Developers"
[12]: http://dom.spec.whatwg.org/ "DOM Libing Standard"
[13]: http://creativecommons.org/licenses/by-nc-nd/3.0/ "Creative Commons Attribution-Noncommercial-No Derivative Works 3.0"
[14]: http://oreilly.com/ "O'Reilly"