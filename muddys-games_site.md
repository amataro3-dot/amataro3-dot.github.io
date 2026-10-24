# muddys-games.com サイトのコード(引き継ぎ用)

新しいスレッドで、このMDを添付して「〇〇を変えたい」と伝えれば続きができます。

## 基本情報

| 項目 | 内容 |
|---|---|
| サイト名 | Muddy's Games(マディーズゲームス) |
| URL | https://muddys-games.com/ |
| リポジトリ | https://github.com/amataro3-dot/amataro3-dot.github.io (GitHub Pages、main / root) |
| ドメイン | Cloudflare で取得。DNS: A `@` → 185.199.108〜111.153 の4つ、CNAME `www` → amataro3-dot.github.io(全部 DNS only=グレーの雲) |
| 運営者名 | muddys-games運営(個人) |
| お問い合わせ | Googleフォーム https://forms.gle/QE6GbJDvfAFDAYrm8 |
| AdSense | パブリッシャーID `ca-pub-8070609230129968`。2026/10/19 に審査をリクエスト済み |

## 公開中のゲーム(同じアカウントの別リポジトリ)

| ゲーム | URL | リポジトリ | 遊び方ページ |
|---|---|---|---|
| Labyrinth .VS | /labyrinth/ | labyrinth | howto-labyrinth.html |
| Party-Arcade | /party-arcade/ | party-arcade | howto-party-arcade.html |
| お絵描き伝言ゲーム | /oekaki/ | oekaki | howto-oekaki.html |

- 各ゲームの画面の下には「Muddy's Games トップ」「プライバシーポリシー」へのリンクを入れてある。
- 3つとも Firebase Realtime Database(プロジェクト labyrinth-game-bc5aa)を使う。
- 富豪大富豪(fugo-daifugo)は作成中のため、トップには載せていない。完成したら、トップにカードと遊び方ページを足す。

## 守ること

1. `index.html` の `<head>` にある AdSense のコード(`adsbygoogle.js?client=ca-pub-8070609230129968`)は消さない。
2. `ads.txt` と `CNAME` は消さない。
3. 全ページの下に、運営者情報・お問い合わせ・プライバシーポリシーへのリンク(footer)を置く。
4. 作りかけのページは公開しない(AdSenseの審査・規約のため)。
5. ゲームを追加したら、トップ(`index.html`)のカード、`about.html` の「公開中のゲーム」、遊び方ページを足す。
6. 広告をゲーム画面に置くときは、ボタンの近くに置かない(誤タップは規約違反)。
7. 編集はスマホのGitHubで行う。変更は「ファイル全体のコード」で渡すと貼りやすい。長いファイルは、ファイルで送ってアップロードする。

## ファイル一覧

| ファイル | 中身 |
|---|---|
| index.html | トップ(ゲーム一覧、AdSenseコード入り) |
| howto-labyrinth.html | Labyrinth .VS の遊び方 |
| howto-party-arcade.html | Party-Arcade の遊び方(2026/10/20 更新: 14ゲーム・結果の数字の意味・点数のしくみ) |
| howto-oekaki.html | お絵描き伝言ゲームの遊び方 |
| about.html | 運営者情報 |
| contact.html | お問い合わせ |
| privacy.html | プライバシーポリシー |
| ads.txt | AdSense の証明 |
| CNAME | 独自ドメイン(GitHubが自動で作ったもの) |
| README.md | 中身なし(リポジトリ作成時のもの) |

---

## index.html

```html
<!doctype html>
<html lang="ja"><head><meta charset="utf-8">
<title>Muddy's Games｜スマホで遊べる無料ブラウザゲーム</title>
<meta name="viewport" content="width=device-width,initial-scale=1">
<meta name="description" content="Muddy's Gamesは、スマホのブラウザですぐ遊べる無料ゲームのサイトです。">
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-8070609230129968" crossorigin="anonymous"></script>
<style>
body{margin:0 auto;max-width:560px;padding:16px;font:16px/1.7 sans-serif;background:#f7f7f2;color:#222}
h1{text-align:center;font-size:28px;margin:16px 0 4px}
.lead{text-align:center;color:#555;margin:0 0 20px}
.card{background:#fff;border-radius:12px;padding:16px;margin:0 0 14px;box-shadow:0 1px 4px #0002}
.card h2{margin:0 0 6px;font-size:20px}
.card p{margin:0 0 12px}
.btns{display:flex;gap:8px}
.play,.how{flex:1;display:block;text-align:center;text-decoration:none;padding:10px;border-radius:8px;font-weight:700}
.play{background:#2874a6;color:#fff}
.how{background:#fff;color:#2874a6;border:2px solid #2874a6}
footer{margin-top:28px;text-align:center;font-size:14px;color:#666}
footer a{color:#2874a6;margin:0 6px;white-space:nowrap}
</style></head><body>
<h1>Muddy's Games</h1>
<p class="lead">スマホのブラウザで、すぐ遊べる無料ゲーム。<br>アプリのインストールはいりません。</p>

<div class="card"><h2>Labyrinth .VS</h2>
<p>相手に見えない壁をしかけた6×6の迷路で、先にゴールしたほうの勝ち！友だちとオンライン対戦も、コンピューター戦もできます。</p>
<div class="btns"><a class="play" href="/labyrinth/">遊ぶ</a><a class="how" href="/howto-labyrinth.html">遊び方</a></div></div>

<div class="card"><h2>Party-Arcade</h2>
<p>ラウンドごとに色々なミニゲームをこなして、チャンピオンになろう！最大8人で遊べます。</p>
<div class="btns"><a class="play" href="/party-arcade/">遊ぶ</a><a class="how" href="/howto-party-arcade.html">遊び方</a></div></div>

<div class="card"><h2>お絵描き伝言ゲーム</h2>
<p>お題を描いて、みんなに伝えよう！！2〜8人で遊べます。</p>
<div class="btns"><a class="play" href="/oekaki/">遊ぶ</a><a class="how" href="/howto-oekaki.html">遊び方</a></div></div>

<footer>
<a href="/about.html">運営者情報</a><a href="/contact.html">お問い合わせ</a><a href="/privacy.html">プライバシーポリシー</a>
<p>© 2026 muddys-games運営</p>
</footer>
</body></html>
```

## howto-labyrinth.html

```html
<!doctype html>
<html lang="ja"><head><meta charset="utf-8">
<title>Labyrinth .VS 遊び方｜Muddy's Games</title>
<meta name="viewport" content="width=device-width,initial-scale=1">
<meta name="description" content="Labyrinth .VSの遊び方。相手に見えない壁をしかけた6×6の迷路で、先にゴールを目指す対戦ゲームのルールを説明します。">
<style>
body{margin:0 auto;max-width:560px;padding:16px;font:16px/1.8 sans-serif;background:#f7f7f2;color:#222}
h1{font-size:24px;margin:12px 0 4px}
.lead{color:#555;margin:0 0 16px}
h2{font-size:18px;margin:28px 0 8px;border-left:5px solid #2874a6;padding-left:8px}
h3{font-size:16px;margin:16px 0 4px}
.box{background:#fff;border-radius:12px;padding:4px 16px 16px;box-shadow:0 1px 4px #0002}
a{color:#2874a6}
ol,ul{padding-left:1.3em;margin:6px 0}li{margin:3px 0}
table{width:100%;border-collapse:collapse;font-size:14px;margin:8px 0}
td,th{border-bottom:1px solid #ddd;padding:5px 4px;text-align:left;vertical-align:top}th{background:#f0f4f8}
.play{display:block;text-align:center;background:#2874a6;color:#fff;text-decoration:none;padding:12px;border-radius:8px;font-weight:700;margin:20px 0}
.tip{background:#fff8e1;border-radius:8px;padding:8px 12px;margin:10px 0;font-size:15px}
footer{margin-top:28px;text-align:center;font-size:14px;color:#666}
footer a{margin:0 6px;white-space:nowrap}
</style></head><body>
<p><a href="/">← Muddy's Games トップ</a></p>
<h1>Labyrinth .VS の遊び方</h1>
<p class="lead">相手に見えない壁をしかけた迷路で、先にゴールしたほうの勝ち。記憶力と読み合いの対戦ゲームです。</p>
<a class="play" href="/labyrinth/">Labyrinth .VS で遊ぶ</a>
<div class="box">

<h2>どんなゲーム?</h2>
<p>おたがいに、6×6マスの迷路を作ります。迷路には「スタート(S)」「ゴール(G)」と、何枚かの「壁」があります。相手に見えるのはSとGの場所だけで、壁の場所はひみつです。</p>
<p>交代で相手の迷路に入り、見えない壁にぶつかりながら道を探します。先に相手の迷路のゴールにたどり着いた人の勝ちです。</p>

<h2>遊べる人数</h2>
<table>
<tr><th>形式</th><th>人数</th><th>内容</th></tr>
<tr><td>シングル</td><td>2人</td><td>1対1で、おたがいの迷路を攻める</td></tr>
<tr><td>ダブルス</td><td>4人</td><td>2人1チームで迷路を作り、交代で動かす</td></tr>
<tr><td>マルチ</td><td>3〜8人</td><td>出題者1人の迷路に、挑戦者みんなで挑む</td></tr>
<tr><td>コンピューター戦</td><td>1人</td><td>ルームなしで、すぐに遊べる</td></tr>
</table>
<p>1つのルームには最大8人まで入れます。対戦しない人は「観戦」として、ゲームを見ていられます。</p>

<h2>はじめかた</h2>
<ol>
<li>名前を入れて「ルームを作成」を押します。</li>
<li>画面に出た4けたのルームIDを、友だちに伝えます。</li>
<li>友だちはIDを入れて「入室」を押します。</li>
<li>ルームを作った人(管理者)が、形式や壁の枚数を決めて「ゲームスタート」を押します。</li>
</ol>

<h2>迷路の作り方</h2>
<ul>
<li>「S」「G」のボタンを選んでマスをタップし、スタートとゴールを置きます。</li>
<li>「壁」を選んで、マスとマスのあいだをタップすると壁が置けます。もう一度タップすると外せます。</li>
<li>壁の枚数は、管理者が10〜20枚から決めます。いちばん外側のふちには置けません。</li>
<li>スタートからゴールへ、必ず行ける道を1本は残します(行けないときは自動で教えてくれます)。</li>
<li>置き終わったら「準備完了」を押します。</li>
</ul>

<h2>対戦のルール</h2>
<ul>
<li>先攻・後攻はランダムで決まります。</li>
<li>自分の番になったら、となりのマスをタップして1マスずつ進みます。</li>
<li>壁にぶつかるまでは、何マスでも続けて進めます。ぶつかったら相手の番です。</li>
<li>ぶつかった壁は赤で表示されて、覚えておけます。次の番は、止まった場所から続けます。</li>
<li>来た道を戻ってもかまいません。</li>
</ul>

<h2>勝ち負けの決まり</h2>
<ul>
<li>後攻が先にゴールしたら、後攻の勝ちです。</li>
<li>先攻が先にゴールしたら「サドンデス」。後攻に最後の1ターンがあたえられます。後攻が一度も壁にぶつからずにゴールできれば引き分け、できなければ先攻の勝ちです。</li>
<li>先攻と後攻で手番の回数がそろうので、公平に戦えます。</li>
</ul>

<h2>ダブルス</h2>
<p>A1・A2とB1・B2の2チームに分かれます。チームの2人で、1つの迷路を一緒に作ります。スタート担当とゴール担当が決まり、壁は2人で1枚ずつ交代で置きます。対戦では、A1→B1→A2→B2 のように、メンバーが交代でコマを動かします。</p>

<h2>マルチ</h2>
<ul>
<li>出題者が1人で迷路を作り、ほかの全員(挑戦者)がその迷路に挑みます。</li>
<li>挑戦者は順番に動きます。1回の番で進めるのは最大2マスです。</li>
<li>だれかがぶつかった壁は、全員に見えるようになります。ほかの人の失敗も手がかりになります。</li>
<li>全員が1回ずつ動くと「1周」。管理者が決めた周の上限(15〜20周)までに、だれもゴールできなければ出題者の勝ちです。</li>
</ul>

<h2>コインバトル(オプション)</h2>
<p>管理者がオンにすると、全員がコイン5枚を持ってスタートします。勝つと+2枚、負けると−2枚。観戦している人は、どちらが勝つかにコインを1枚賭けられます。さらに「ボーナスウォール」をオンにすると、観戦者が「ここにぶつかりそう」と思う壁を1枚選び、当たればボーナスがもらえます。</p>

<h2>大会モード</h2>
<p>4人以上いれば、トーナメント、リーグ戦(シングル・ダブルス)、公式戦(試合ごとに形式を選ぶ)で遊べます。左上の「大会表」で、いつでも順位を確認できます。</p>

<h2>コンピューター戦</h2>
<p>強さは「よわい」「ふつう」「つよい」の3段階です。「ふつう」はぶつかった壁を覚え、「つよい」はさらにゴールまでの近道を探してきます。ルールを覚えるのにぴったりです。</p>

<h2>勝つためのコツ</h2>
<div class="tip">💡 壁はゴールのまわりだけに固めず、遠回りの道に分けて置くと、相手が迷いやすくなります。</div>
<div class="tip">💡 赤くなった壁の位置から、「ここに壁があるなら、道はこっちかも」と相手の作り方を読むのが勝負の分かれ目です。</div>
<div class="tip">💡 後攻のときは、サドンデスで1回もぶつからずにゴールできるよう、安全な道を覚えておきましょう。</div>
</div>
<a class="play" href="/labyrinth/">Labyrinth .VS で遊ぶ</a>
<footer>
<a href="/about.html">運営者情報</a><a href="/contact.html">お問い合わせ</a><a href="/privacy.html">プライバシーポリシー</a>
<p>© 2026 muddys-games運営</p>
</footer>
</body></html>
```

## howto-party-arcade.html

```html
<!doctype html>
<html lang="ja"><head><meta charset="utf-8">
<title>Party-Arcade 遊び方｜Muddy's Games</title>
<meta name="viewport" content="width=device-width,initial-scale=1">
<meta name="description" content="Party-Arcadeの遊び方。最大8人で、反射神経・感覚・記憶力を競う14種類のミニゲームに挑戦する対戦パーティーゲームのルールを説明します。">
<style>
body{margin:0 auto;max-width:560px;padding:16px;font:16px/1.8 sans-serif;background:#f7f7f2;color:#222}
h1{font-size:24px;margin:12px 0 4px}
.lead{color:#555;margin:0 0 16px}
h2{font-size:18px;margin:28px 0 8px;border-left:5px solid #2874a6;padding-left:8px}
h3{font-size:16px;margin:16px 0 4px}
.box{background:#fff;border-radius:12px;padding:4px 16px 16px;box-shadow:0 1px 4px #0002}
a{color:#2874a6}
ol,ul{padding-left:1.3em;margin:6px 0}li{margin:3px 0}
table{width:100%;border-collapse:collapse;font-size:14px;margin:8px 0}
td,th{border-bottom:1px solid #ddd;padding:5px 4px;text-align:left;vertical-align:top}th{background:#f0f4f8}
.play{display:block;text-align:center;background:#2874a6;color:#fff;text-decoration:none;padding:12px;border-radius:8px;font-weight:700;margin:20px 0}
.nw{white-space:nowrap}
.res{display:block;margin-top:4px;color:#555;font-size:13px}
.tip{background:#fff8e1;border-radius:8px;padding:8px 12px;margin:10px 0;font-size:15px}
footer{margin-top:28px;text-align:center;font-size:14px;color:#666}
footer a{margin:0 6px;white-space:nowrap}
</style></head><body>
<p><a href="/">← Muddy's Games トップ</a></p>
<h1>Party-Arcade の遊び方</h1>
<p class="lead">ラウンドごとにちがうミニゲームで勝負して、合計ポイントでチャンピオンを決めるパーティーゲームです。</p>
<a class="play" href="/party-arcade/">Party-Arcade で遊ぶ</a>
<div class="box">

<h2>遊べる人数</h2>
<p>1つのルームで最大8人まで、全員同時に遊べます。1人で遊べる「練習モード」もあります。</p>

<h2>はじめかた</h2>
<ol>
<li>名前を入れて、ルームを作ります。作った人が管理者になります。</li>
<li>4けたのルームIDを友だちに伝えて、入室してもらいます。</li>
<li>管理者がロビーでモードを決めて、スタートします。</li>
</ol>

<h2>モード</h2>
<h3>アーケード</h3>
<p>4〜8ラウンドのあいだ、毎回ちがうミニゲームがランダムに出ます。全部のゲームが1回ずつ出るまで同じゲームは出ないので、いろいろなゲームで勝負できます。合計ポイントがいちばん多い人が優勝です。</p>
<ul>
<li><b>ダブルアップ</b>:どこか1ラウンドだけ、ポイントが2倍。ゲームの直前に発表されます。</li>
<li><b>ファイナルアップ</b>:最後のラウンドのポイントが2倍。最後まで逆転のチャンスがあります。</li>
</ul>
<h3>ソロゲーム</h3>
<p>好きなミニゲームを1つ選んで、全員で1回だけ遊びます。ポイントはつきません。気になるゲームでサクッと勝負したいときに。</p>
<h3>練習モード</h3>
<p>ルームに入らずに、1人でミニゲームを練習できます。記録は保存されません。</p>

<h2>ポイントのつき方</h2>
<table>
<tr><th>順位</th><td>1位</td><td>2位</td><td>3位</td><td>4位</td><td>5位</td><td>6位</td><td>7位</td><td>8位</td></tr>
<tr><th>ポイント</th><td>10</td><td>8</td><td>6</td><td>5</td><td>4</td><td>3</td><td>2</td><td>1</td></tr>
</table>
<p>同じ記録の人は同じ順位です。失敗したときや、時間内に終わらなかったときは0ポイントになります。どんな記録で順位が決まるかは、下の「ミニゲーム一覧」と「点数のしくみ」を見てください。</p>

<h2>ミニゲーム一覧</h2>
<p>各ゲームの前に5秒のカウントダウンがあり、そのあいだにルールが表示されます。「結果」は、ゲームのあとの結果画面に出る数字の意味です。この数字で順位が決まります。</p>
<table>
<tr><th>ゲーム</th><th>内容</th></tr>
<tr><td>5秒ジャスト</td><td>5秒ぴったりだと思ったらSTOP。数字はとちゅうで消えます。<span class="res">結果: 5秒とのずれ(秒)。小さいほど上位。12秒たっても止めないと0pt。</span></td></tr>
<tr><td>反射神経</td><td>赤から緑に変わったらすぐタップ。早すぎるとフライングです。<span class="res">結果: 緑になってからタップするまでの時間(ms)。速いほど上位。フライング・3秒以上は0pt。</span></td></tr>
<tr><td>〇センチを描け!</td><td>お題の長さ(1〜6cm)の線を、目分量で描きます。<span class="res">結果: 描いた線(始点から終点まで)とお題の長さの差(cm)。小さいほど上位。描かないと0pt。</span></td></tr>
<tr><td>キレイに切って!</td><td>円を3〜9個に、できるだけ同じ大きさで切り分けます。<span class="res">結果: 1切れずつの大きさが、ぴったり等分からずれた割合の平均(%)。小さいほど上位。時間内に切り終わらないと0pt。</span></td></tr>
<tr><td>角度を描け!</td><td>お題の角度になるように線を引きます。<span class="res">結果: 描いた角度とお題の角度の差(°)。小さいほど上位。</span></td></tr>
<tr><td>旗揚げゲーム!!</td><td>審判のお題(「赤上げて」「白下げない」など)どおりに旗を上げ下げします。下の赤・白のボタンを押しているあいだが「上げる」、離すと「下げる」。「〜ない」のひっかけや、お題に出ていない旗は、一瞬でも動かしたらアウト。だんだん速くなります。<span class="res">結果: 点数(20点+連続正解ボーナス、満点35点)。高いほど上位。くわしくは下の「点数のしくみ」へ。</span></td></tr>
<tr><td>色ちがい探し!</td><td>マスの中から、ほんの少しだけ色がちがうものを探します。<span class="res">結果: 15秒で正解した数。多いほど上位。0問は0pt。</span></td></tr>
<tr><td>数字タッチ!</td><td>1〜16の数字を、小さい順にできるだけ早くタッチ。<span class="res">結果: 16まで押すのにかかった秒数。速いほど上位。17秒で終わらなかった人は「〇個まで」と出て、押せた数で順位(クリアした人より下)。</span></td></tr>
<tr><td>よけろ!</td><td>降ってくる岩や板を、指を左右に動かしてよけ続けます。<span class="res">結果: 生き残った秒数。長いほど上位。15秒でクリア。</span></td></tr>
<tr><td>マディーズバーガーを作ろう!</td><td>上から落ちてくる具材をお皿で受け止めて、ハンバーガーを積み上げます。真ん中に乗せるほど高得点。傾きすぎると崩れます。<span class="res">結果: 点数(満点820点)。高いほど上位。くわしくは下の「点数のしくみ」へ。</span></td></tr>
<tr><td>ジャックを注げ!</td><td>ボトルを押しているあいだだけ注げます。量の数字は出ないので、グラスの液面を見てお題の量で「決定」。あふれたら失敗です。<span class="res">結果: 注いだ量とお題の量の差(ml)。小さいほど上位。注がなかった・あふれたときは0pt。</span></td></tr>
<tr><td>俺のハンバーグを焼け!</td><td>3個のハンバーグをタップでひっくり返し、もう一度タップでお皿へ。ハンバーグの色は、いま焼けている下の面の色です(ひっくり返すと生の色にもどります)。出てくる時間も焼ける速さもバラバラで、途中で速さが変わります。ジュージューの粒が増えたら、速く焼けているしるし。両面ともお題の焼き色に近づけます。焦がしたらダメ!<span class="res">結果: お題の焼き色との差の平均。小さいほど上位。くわしくは下の「点数のしくみ」へ。</span></td></tr>
<tr><td>だるまさんがころんだ!</td><td>左右のボタンを交互に連打して、鬼に近づきます。鬼が振り向いているときに押すとアウト。鬼にタッチできればゴールです。<span class="res">結果: ゴールした人はタイム、ゴールできなかった人は鬼までの残りの距離(m)。くわしくは下の「点数のしくみ」へ。</span></td></tr>
<tr><td>南インド風カレーを作ろう!</td><td>鍋に入るスパイスを順番どおりに覚えて、棚から同じ順に選びます。<span class="res">結果: 点数(満点は個数×2)。高いほど上位。くわしくは下の「点数のしくみ」へ。</span></td></tr>
</table>

<h2>点数のしくみ(くわしく)</h2>
<h3>旗揚げゲーム!!</h3>
<ul>
<li>お題は全部で20点分。「赤上げて」のような1つだけのお題は1点、「赤上げないで 白下げて」のような赤と白のお題は2点(赤と白で別々に判定)です。</li>
<li>「上げて」「下げて」: 判定の瞬間に、その状態になっていれば正解。もうその状態のときは、一瞬でも動かしたらアウト。</li>
<li>「上げない」「下げない」: その旗を一瞬でも動かしたらアウト。</li>
<li>お題に出ていない旗を動かしても、その部分はアウトです。</li>
<li>連続正解ボーナス: 4連続 +1、8連続 +2、12連続 +3、16連続 +4、20連続(パーフェクト) +5。まちがえると連続は0にもどります。</li>
<li>満点は 20 + 15 = <b>35点</b>。0点は0ptです。同じ点数は同じ順位です。</li>
</ul>

<h3>マディーズバーガーを作ろう!</h3>
<table>
<tr><th>内容</th><th>点</th></tr>
<tr><td>最後までお皿に乗っている具材</td><td class="nw">1個 50点</td></tr>
<tr><td>乗せ方(着地した瞬間に決まり、あとで崩れても残る)</td><td class="nw">Perfect +30<br>Good +15<br>ギリギリ +0</td></tr>
<tr><td>完成(最後に上のバンズが乗っている)</td><td>+100</td></tr>
<tr><td>落とした具材(崩れて落ちた分も)</td><td>0点</td></tr>
</table>
<p>具材は全部で9個なので、満点は 450 + 270 + 100 = <b>820点</b>。同じ点数のときは、ずれが小さかった人が上位です。0点は0ptになります。</p>

<h3>俺のハンバーグを焼け!</h3>
<p>焼け具合を0〜100の数字で表します。0が生、100が焦げです。</p>
<table>
<tr><th>お題</th><th>焼け具合</th></tr>
<tr><td>レア</td><td>30</td></tr>
<tr><td>ミディアムレア</td><td>45</td></tr>
<tr><td>ミディアム</td><td>60</td></tr>
<tr><td>ウェルダン</td><td>80</td></tr>
</table>
<ul>
<li>3個のハンバーグの両面、合わせて6面それぞれで、お題の数字との差を出します。</li>
<li>その6つの差の平均が「結果」の数字です。小さいほど上位です。</li>
<li>焦げたハンバーグと、時間内にお皿に乗せられなかったハンバーグは、両面とも差100として計算します。</li>
<li>3個とも焦げたら0ptです。</li>
</ul>
<p>例:お題がミディアム(60)で、1個目を表58・裏63で焼いたら、差は2と3です。</p>

<h3>だるまさんがころんだ!</h3>
<ul>
<li>鬼にタッチできた人(ゴール)は、必ずゴールできなかった人より上位です。ゴールした人どうしは、タイムが速いほど上位です。</li>
<li>ゴールできなかった人(バレた・時間切れ)は、「あと〇m」の距離が短いほど上位です。鬼までは20mあります。</li>
<li>スタートから1歩も進めなかったときは0ptです。</li>
</ul>

<h3>南インド風カレーを作ろう!</h3>
<table>
<tr><th>判定</th><th>点</th></tr>
<tr><td>◎ スパイスも順番も合っている</td><td>2点</td></tr>
<tr><td>○ レシピに入っているが、順番がちがう</td><td>1点</td></tr>
<tr><td>× レシピに入っていない(空いている枠も)</td><td>0点</td></tr>
</table>
<p>スパイスは6〜8個なので、満点は個数×2(8個なら16点)です。同じスパイスが2回入るときは、2回とも当てれば2個とも点になります。同じ点数のときは、早く「完成!」を押した人が上位です。0点は0ptになります。</p>
<p>例:レシピが「クミン → カレーリーフ → ターメリック」で、答えが「カレーリーフ → クミン → ターメリック」なら、○ ○ ◎ で4点です。</p>

<h2>楽しむためのコツ</h2>
<div class="tip">💡 カウントダウン中のルール説明をしっかり読むのが勝利への近道。初めてのゲームは練習モードで試しておくと安心です。</div>
<div class="tip">💡 ダブルアップやファイナルアップをオンにすると、最後まで順位が入れかわって盛り上がります。</div>
<div class="tip">💡 新しいゲームが出てこないときは、ブラウザのタブを一度閉じて開き直してください。古いデータが残っていることがあります。</div>
<div class="tip">💡 通信が一瞬切れても、ページを開き直せば同じルームに戻れます。</div>
</div>
<a class="play" href="/party-arcade/">Party-Arcade で遊ぶ</a>
<footer>
<a href="/about.html">運営者情報</a><a href="/contact.html">お問い合わせ</a><a href="/privacy.html">プライバシーポリシー</a>
<p>© 2026 muddys-games運営</p>
</footer>
</body></html>
```

## howto-oekaki.html

```html
<!doctype html>
<html lang="ja"><head><meta charset="utf-8">
<title>お絵描き伝言ゲーム 遊び方｜Muddy's Games</title>
<meta name="viewport" content="width=device-width,initial-scale=1">
<meta name="description" content="お絵描き伝言ゲームの遊び方。お題を絵だけで次の人へつなぎ、最後の人が答えを当てる2〜8人用のオンラインゲームのルールを説明します。">
<style>
body{margin:0 auto;max-width:560px;padding:16px;font:16px/1.8 sans-serif;background:#f7f7f2;color:#222}
h1{font-size:24px;margin:12px 0 4px}
.lead{color:#555;margin:0 0 16px}
h2{font-size:18px;margin:28px 0 8px;border-left:5px solid #2874a6;padding-left:8px}
h3{font-size:16px;margin:16px 0 4px}
.box{background:#fff;border-radius:12px;padding:4px 16px 16px;box-shadow:0 1px 4px #0002}
a{color:#2874a6}
ol,ul{padding-left:1.3em;margin:6px 0}li{margin:3px 0}
table{width:100%;border-collapse:collapse;font-size:14px;margin:8px 0}
td,th{border-bottom:1px solid #ddd;padding:5px 4px;text-align:left;vertical-align:top}th{background:#f0f4f8}
.play{display:block;text-align:center;background:#2874a6;color:#fff;text-decoration:none;padding:12px;border-radius:8px;font-weight:700;margin:20px 0}
.tip{background:#fff8e1;border-radius:8px;padding:8px 12px;margin:10px 0;font-size:15px}
footer{margin-top:28px;text-align:center;font-size:14px;color:#666}
footer a{margin:0 6px;white-space:nowrap}
</style></head><body>
<p><a href="/">← Muddy's Games トップ</a></p>
<h1>お絵描き伝言ゲームの遊び方</h1>
<p class="lead">お題を絵だけでリレーして、最後の人が答えを当てるゲームです。絵がどんどん変わっていく様子を、最後にみんなで見て笑えます。</p>
<a class="play" href="/oekaki/">お絵描き伝言ゲームで遊ぶ</a>
<div class="box">

<h2>遊べる人数</h2>
<p>2〜8人です。人数が多いほど、絵が変わっていく楽しさが大きくなります。</p>

<h2>はじめかた</h2>
<ol>
<li>名前を入れて「部屋を作る」を押します。</li>
<li>画面に出た4けたの部屋コードを、友だちに伝えます。</li>
<li>友だちはコードを入れて「入室する」を押します。</li>
<li>最初に部屋に入った人(ホスト)が、お題のジャンルを選んで「ゲーム開始」を押します。</li>
</ol>

<h2>ゲームの流れ</h2>
<p>順番はスタート時にランダムで決まります。</p>
<ol>
<li><b>1人目</b>:お題を見て、30秒で絵を描きます。</li>
<li><b>2人目</b>:1人目の絵を10秒だけ見ます。絵が消えたら、思い出しながら30秒で描きます(お題は見られません)。</li>
<li><b>3人目からも同じ</b>:前の人の絵を見て、覚えて、描く、をくり返します。</li>
<li><b>最後の人</b>:前の人の絵を見て、お題が何だったかを30秒で答えます。</li>
</ol>
<p>描き終わったら「完了」を押すと、時間が残っていても次の人に進みます。</p>

<h2>絵の描き方</h2>
<ul>
<li>指でなぞると線が引けます。</li>
<li>色は黒・赤・青・緑・黄・白(消しゴム代わり)の6色。線の太さは「細」「太」で切りかえます。</li>
<li>「1つ戻す」で最後の線を消せます。「全部消す」で描き直せます。</li>
</ul>

<h2>正解の判定</h2>
<ul>
<li>ひらがなとカタカナのちがい、空白や「!」「?」などの記号は気にせず判定します。</li>
<li>お題によっては、別の読み方でも正解になります。</li>
<li>判定に納得できないときは、ホストが結果画面で「正解にする/不正解にする」を切りかえられます。</li>
</ul>

<h2>結果発表</h2>
<p>お題と最後の人の答え、そして全員の絵が順番に並びます。「最初から再生」を押すと、それぞれの絵が描かれた順番どおりにアニメーションで再生されます。どこでお題が変わってしまったのか、みんなで探してみましょう。</p>

<h2>楽しむためのコツ</h2>
<div class="tip">💡 細かく描くより、ひと目で分かる特ちょうを大きく描くほうが伝わります。</div>
<div class="tip">💡 10秒で絵を覚えるのは意外とむずかしい! 形だけでなく、色や数も覚えておくのがポイントです。</div>
<div class="tip">💡 わざと伝わらなくても大丈夫。絵がどんどん変わっていくのが、このゲームのいちばんの楽しさです。</div>
</div>
<a class="play" href="/oekaki/">お絵描き伝言ゲームで遊ぶ</a>
<footer>
<a href="/about.html">運営者情報</a><a href="/contact.html">お問い合わせ</a><a href="/privacy.html">プライバシーポリシー</a>
<p>© 2026 muddys-games運営</p>
</footer>
</body></html>
```

## about.html

```html
<!doctype html>
<html lang="ja"><head><meta charset="utf-8">
<title>運営者情報｜Muddy's Games</title>
<meta name="viewport" content="width=device-width,initial-scale=1">
<style>
body{margin:0 auto;max-width:560px;padding:16px;font:16px/1.8 sans-serif;background:#f7f7f2;color:#222}
h1{font-size:24px;margin:16px 0}
h2{font-size:18px;margin:24px 0 6px;border-left:5px solid #2874a6;padding-left:8px}
.box{background:#fff;border-radius:12px;padding:16px;box-shadow:0 1px 4px #0002}
a{color:#2874a6}
footer{margin-top:28px;text-align:center;font-size:14px;color:#666}
footer a{margin:0 6px;white-space:nowrap}
</style></head><body>
<p><a href="/">← Muddy's Games トップ</a></p>
<h1>運営者情報</h1>
<div class="box">
<h2>サイト名</h2><p>Muddy's Games(マディーズゲームス)</p>
<h2>URL</h2><p>https://muddys-games.com/</p>
<h2>運営者</h2><p>muddys-games運営</p>
<h2>このサイトについて</h2>
<p>Muddy's Gamesは、スマホのブラウザですぐに遊べる、無料のオリジナルゲームを公開している個人運営のサイトです。友だちや家族と気軽に盛り上がれるゲームを、ひとつずつ手作りしています。</p>
<h2>公開中のゲーム</h2>
<p><a href="/labyrinth/">Labyrinth .VS</a> … 見えない壁の迷路で対戦するゲーム<br>
<a href="/party-arcade/">Party-Arcade</a> … ミニゲームでチャンピオンを目指すゲーム<br>
<a href="/oekaki/">お絵描き伝言ゲーム</a> … お題を絵で伝えるゲーム</p>
<h2>お問い合わせ</h2>
<p>ご意見・不具合のご報告は、<a href="/contact.html">お問い合わせページ</a>からお願いします。</p>
</div>
<footer>
<a href="/about.html">運営者情報</a><a href="/contact.html">お問い合わせ</a><a href="/privacy.html">プライバシーポリシー</a>
<p>© 2026 muddys-games運営</p>
</footer>
</body></html>
```

## contact.html

```html
<!doctype html>
<html lang="ja"><head><meta charset="utf-8">
<title>お問い合わせ｜Muddy's Games</title>
<meta name="viewport" content="width=device-width,initial-scale=1">
<style>
body{margin:0 auto;max-width:560px;padding:16px;font:16px/1.8 sans-serif;background:#f7f7f2;color:#222}
h1{font-size:24px;margin:16px 0}
.box{background:#fff;border-radius:12px;padding:16px;box-shadow:0 1px 4px #0002}
a{color:#2874a6}
.btn{display:block;text-align:center;background:#2874a6;color:#fff;text-decoration:none;padding:12px;border-radius:8px;font-weight:700;margin:16px 0}
footer{margin-top:28px;text-align:center;font-size:14px;color:#666}
footer a{margin:0 6px;white-space:nowrap}
</style></head><body>
<p><a href="/">← Muddy's Games トップ</a></p>
<h1>お問い合わせ</h1>
<div class="box">
<p>ゲームの不具合のご報告、ご意見・ご感想は、下のフォームからお送りください。</p>
<a class="btn" href="https://forms.gle/QE6GbJDvfAFDAYrm8" target="_blank" rel="noopener">お問い合わせフォームを開く</a>
<p>・返信がほしい方は、フォームにメールアドレスをご記入ください。<br>・すべてのお問い合わせに返信できるとは限りません。あらかじめご了承ください。<br>・送っていただいた内容の取り扱いは、<a href="/privacy.html">プライバシーポリシー</a>をご覧ください。</p>
</div>
<footer>
<a href="/about.html">運営者情報</a><a href="/contact.html">お問い合わせ</a><a href="/privacy.html">プライバシーポリシー</a>
<p>© 2026 muddys-games運営</p>
</footer>
</body></html>
```

## privacy.html

```html
<!doctype html>
<html lang="ja"><head><meta charset="utf-8">
<title>プライバシーポリシー｜Muddy's Games</title>
<meta name="viewport" content="width=device-width,initial-scale=1">
<style>
body{margin:0 auto;max-width:560px;padding:16px;font:16px/1.8 sans-serif;background:#f7f7f2;color:#222}
h1{font-size:24px;margin:16px 0}
h2{font-size:18px;margin:24px 0 6px;border-left:5px solid #2874a6;padding-left:8px}
.box{background:#fff;border-radius:12px;padding:16px;box-shadow:0 1px 4px #0002}
a{color:#2874a6;word-break:break-all}
footer{margin-top:28px;text-align:center;font-size:14px;color:#666}
footer a{margin:0 6px;white-space:nowrap}
</style></head><body>
<p><a href="/">← Muddy's Games トップ</a></p>
<h1>プライバシーポリシー</h1>
<div class="box">
<p>Muddy's Games(以下「当サイト」)は、利用者の情報を次のとおり取り扱います。</p>

<h2>1. 広告について</h2>
<p>当サイトは、Google が提供する広告配信サービス「Google AdSense」を利用しています(利用予定を含みます)。</p>
<p>Google などの第三者配信事業者は、Cookie(クッキー)を使って、利用者が当サイトや他のサイトに過去にアクセスした情報にもとづいて広告を配信します。Google は広告 Cookie を使うことで、利用者が当サイトや他のサイトにアクセスした際の情報にもとづいて、Google やそのパートナーが適切な広告を表示できるようにしています。</p>
<p>利用者は、<a href="https://adssettings.google.com/" target="_blank" rel="noopener">Google の広告設定</a>で、パーソナライズ広告を無効にできます。また、<a href="https://optout.aboutads.info/" target="_blank" rel="noopener">www.aboutads.info</a> で、第三者配信事業者の Cookie を無効にすることもできます。</p>
<p>Google によるデータの使い方は、<a href="https://policies.google.com/technologies/partner-sites?hl=ja" target="_blank" rel="noopener">Google のポリシーと規約</a>をご覧ください。</p>

<h2>2. ゲームで保存する情報</h2>
<p>オンラインで遊べるゲームでは、対戦や進行のために、入力した名前、ルームの番号、ゲームの進み具合、チャットの内容などを、Google が提供する「Firebase」に保存します。ログインは、個人を特定しない匿名の方式です。保存した情報は、ゲームの運営のためだけに使います。</p>
<p>また、次に開いたときに便利なように、名前や入っていたルームを、利用者の端末(ブラウザ)に保存することがあります。これはブラウザの設定から消すことができます。</p>
<p>チャットや名前に、本名・住所・電話番号などの個人情報は書かないでください。</p>

<h2>3. お問い合わせで受け取る情報</h2>
<p>お問い合わせフォーム(Google フォーム)で送っていただいた名前やメールアドレスなどは、お問い合わせへの返信と、サイトの改善のためだけに使います。</p>

<h2>4. 第三者への提供</h2>
<p>法令にもとづく場合をのぞき、ご本人の同意なく、個人情報を第三者に提供することはありません。</p>

<h2>5. お子さまのご利用について</h2>
<p>中学生以下のお子さまは、保護者の方といっしょにご利用ください。</p>

<h2>6. 免責事項</h2>
<p>当サイトのゲームや情報は、できるかぎり正確に動くよう努めていますが、その内容を保証するものではありません。当サイトの利用によって生じた損害について、当サイトは責任を負いません。当サイトのリンク先のサイトで提供される情報やサービスについても、責任を負いません。</p>

<h2>7. 著作権</h2>
<p>当サイトのゲーム、文章、画像などの著作権は、当サイトの運営者に帰属します。無断での転載・複製はご遠慮ください。</p>

<h2>8. このポリシーの変更</h2>
<p>このポリシーは、必要に応じて内容を変更することがあります。変更後のポリシーは、このページに載せた時点から有効になります。</p>

<h2>9. お問い合わせ先</h2>
<p>このポリシーについてのお問い合わせは、<a href="/contact.html">お問い合わせページ</a>からお願いします。</p>

<p>運営者:muddys-games運営<br>制定日:2026年10月19日</p>
</div>
<footer>
<a href="/about.html">運営者情報</a><a href="/contact.html">お問い合わせ</a><a href="/privacy.html">プライバシーポリシー</a>
<p>© 2026 muddys-games運営</p>
</footer>
</body></html>
```

## ads.txt

```text
google.com, pub-8070609230129968, DIRECT, f08c47fec0942fa0
```

## CNAME

```text
muddys-games.com
```
