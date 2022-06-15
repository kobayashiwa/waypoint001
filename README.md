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
このあとjQueryで「animation-box」が画面指定位置に来たらクラスを付ける。

### jQueryサンプル
```
$(function(){
    $('.animation-box').waypoint(function(direction){
        var activePoint = $(this.element);
        if (direction === 'down') {　//scroll down
            activePoint.addClass('active');
        }
        else{ //scroll up
            activePoint.removeClass('active');
        }
    },{offset : '70%'});
});
```
2行目、functionの引数に「direction」を指定することで下方向へのスクロールか上方向へのスクロールか判別することができる。ここがwaypointの便利なところ。

3行目「animation-box」が複数ある場合でも「var activePoint = $(this.element);」で現在の画面指定位置に来た要素を変数「activePoint」に代入している。これを設定しないと対象の要素が複数ある場合、まだ画面指定位置に来ていない要素にも一気に適用されてしまう。

4行目「if (direction === 'down')」で下方向のスクロールかつ要素が画面指定位置に来たタイミングで「active」というクラスを付けている。逆に上方向へのスクロールで要素が画面位置に来たら「active」クラスを外して元に戻している。

10行目「offset : '70%'」が画面位置の指定。この場合、画面の上から70％のところということになる。「offset : ‘50%’」なら画面の縦中央となる。

# 3.CSSでアニメーションさせる
   
    
### CSSサンプル
```
.animation-box:nth-child(odd){
    background: #eee;
}
 
.animation-box{
    padding: 120px;
    transition:.5s;
}
 
.animation-box.active{
    background: #666;
    color: #fff;
}
```
デフォルトのanimation-boxのスタイルに「transition: .5s;」を設定して0.5秒でアニメーションするようにしている。
    
画面指定位置に来たら付与されるクラスのスタイル「.animation-box.active」で背景色とフォントカラーを変更するようにしている。
