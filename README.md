# testgame
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>逃げる画像ゲーム</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            width: 100vw;
            height: 100vh;
            overflow: hidden; /* スクロールバーが出ないようにする */
            background-color: #f0f0f0;
            font-family: sans-serif;
        }

        #game-target {
            position: absolute;
            cursor: pointer;
            transition: all 0.1s ease-out; /* 少し動きを滑らかにする（お好みで） */
            user-select: none;
            -webkit-user-drag: none;
        }

        .info {
            padding: 10px;
            color: #333;
        }
    </style>
</head>
<body>

    <div class="info">画像をクリックしてね！</div>
    
    <img id="game-target" src="your-image.png" alt="ターゲット" width="100">

    <script>
        const target = document.getElementById('game-target');

        // 画像をランダムな位置に移動させる関数
        function moveImage() {
            // 画面の幅と高さから、画像のサイズ分を引いて範囲を決める
            const maxX = window.innerWidth - target.clientWidth;
            const maxY = window.innerHeight - target.clientHeight;

            // ランダムな座標を計算
            const randomX = Math.floor(Math.random() * maxX);
            const randomY = Math.floor(Math.random() * maxY);

            // スタイルに反映
            target.style.left = randomX + 'px';
            target.style.top = randomY + 'px';
        }

        // クリックした時のイベント
        target.addEventListener('click', () => {
            moveImage();
        });

        // 画像が読み込まれた直後に最初の配置を行う
        window.onload = moveImage;

        // 画面サイズが変わった時も、はみ出さないように調整
        window.onresize = moveImage;
    </script>
</body>
</html>
