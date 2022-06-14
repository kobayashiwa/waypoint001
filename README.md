# waypoint001
タイミングを取得して簡単なアニメーションをさせる

## jQuery】waypoint.jsとCSSでスクロールして画面指定位置で要素をアニメーションさせる

# 1.waypoint.jsを設置
画面の指定位置に要素が入ったことを取得するためwaypoint.jsを使用する。

スクリプトを自前で書いて行うこともできるが、waypoint.jsはスクロールのアップ・ダウンを判別できたりとても便利なプラグインなので試してみる。

ダウンロードしたファイルから、今回は「lib」フォルダの中の「jquery.waypoints.min.js」を使用する。

```
<script type="text/javascript" src="/js/jquery-3.2.1.min.js"></script>
<script type="text/javascript" src="/js/jquery.waypoints.min.js"></script>
```
<head>内にてwaypointを読み込む。今回はjQueryバージョンのwaypointを使用しているので、jQueryもwaypointの前に読み込ませる。
  
# 2.要素が画面指定位置に来たタイミングを取得してクラスを付与
設置ができたら要素が画面指定位置に来たタイミングを取得する。

### HTMLサンプル
```
<div class="animation-box">
    <h2>Section1</h2>
    <p>このボックスが画面上から70％の位置に来たら背景色を変更します。</p>
</div>
```
