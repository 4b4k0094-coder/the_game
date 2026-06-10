<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>跨平台實境解謎遊戲</title>
    <style>
        /* --- 基礎防呆與全螢幕設定 --- */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            user-select: none; /* 防止手機玩家長按文字跳出複製選單 */
        }
        body, html {
            width: 100%;
            height: 100%;
            background-color: #1a1a1a;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
            color: #ffffff;
            overflow: hidden; /* 防止手機版網頁不正常滾動 */
        }

        /* --- 中央遊戲畫布外殼 --- */
        .app-wrapper {
            width: 100%;
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* --- 通用的面板樣式（電腦版限制最大寬高，手機版全螢幕） --- */
        .scene-panel {
            width: 100%;
            height: 100%;
            max-width: 450px;  /* 限制最大寬度，讓電腦版看起來像手機 App */
            max-height: 850px; /* 限制最大高度 */
            background: #2c2c2c;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            padding: 24px;
            transition: all 0.3s ease;
        }

        /* --- 響應式調整：當螢幕夠寬（電腦/平板）時的優化 --- */
        @media (min-width: 768px) {
            .scene-panel {
                border-radius: 16px;
                height: 90%; /* 在電腦上不硬塞滿，留點邊框更好看 */
                border: 2px solid #444;
            }
        }

        /* --- 內容區域 --- */
        .content-area {
            flex-grow: 1;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
        }

        .stage-title {
            font-size: 24px;
            color: #ffb300;
            margin-bottom: 20px;
        }

        .story-text {
            font-size: 16px;
            line-height: 1.6;
            color: #dddddd;
            max-width: 90%;
        }

        /* --- 跨平台大按鈕（適合滑鼠點擊與大拇指按壓） --- */
        .game-btn {
            width: 100%;
            padding: 16px;
            font-size: 18px;
            font-weight: bold;
            color: #1a1a1a;
            background: #ffb300;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            box-shadow: 0 4px 6px rgba(0,0,0,0.2);
            transition: background 0.2s, transform 0.1s;
        }
        .game-btn:hover {
            background: #ffa000;
        }
        .game-btn:active {
            transform: scale(0.98); /* 點擊時的下壓反饋 */
        }
    </style>
</head>
<body>

<div class="app-wrapper">

    <div id="game-container" class="scene-panel">
        <div class="content-area">
            <h2 id="stage-title" class="stage-title">第一關：西市場的異動</h2>
            <p style="color: #888;">[ 這裡放置你的 AR 畫面或解謎互動區 ]</p>
        </div>
        <button class="game-btn" onclick="completeStage(currentStage)">
            完成本關任務
        </button>
    </div>

    <div id="transition-container" class="scene-panel" style="display: none; background: #1e1e1e;">
        <div class="content-area">
            <h2 style="color: #00e676; margin-bottom: 20px;">時空重塑中...</h2>
            <p id="transition-story" class="story-text">過場劇情載入中...</p>
        </div>
        <button id="next-stage-btn" class="game-btn" style="background: #00e676;">
            前往下一關卡
        </button>
    </div>

    <div id="ending-container" class="scene-panel" style="display: none; background: #111;">
        <div class="content-area">
            <h1 style="color: #ff3d00; margin-bottom: 16px;">時空敕令 終局</h1>
            <p class="story-text">恭喜通關！你已成功導正所有時空軌跡，拯救了歷史線。</p>
        </div>
        <button class="game-btn" onclick="restartGame()" style="background: #ffffff; color: #111;">
            重新開始旅程
        </button>
    </div>

</div>

<script>
    // 關卡資料庫
    const gameStages = {
        1: { name: "第一關：西市場的異動", next: 2, story: "成功解開西市場的封印，時空裂縫的軌跡似乎引導你前往下一個地點..." },
        2: { name: "第二關：明鄭敕令的線索", next: 3, story: "尋獲了塵封的關鍵敕令，歷史的真相即將在下一站揭曉..." },
        3: { name: "第三關：大員港風雲", next: 4, story: "成功破解了外商的貿易密碼，下一個時空節點指向了山區..." },
        4: { name: "第四關：噍吧哖的怒火", next: 5, story: "歷史的硝煙散去，抗日事件的記憶已化作你手中前進的力量..." },
        5: { name: "第五關：玉井時空節點", next: 6, story: "時空儀器的指針開始劇烈晃動，核心謎底就在前方..." },
        6: { name: "第六關：大明慈悲的召喚", next: 7, story: "最後的屏障已解除，準備迎來最終的時空審判！" },
        7: { name: "第七關：時空敕令的終局", next: null, story: null }
    };

    let currentStage = 1;

    function completeStage(stageId) {
        if (stageId < 7) {
            // 1~6關：顯示過場跳轉頁面
            document.getElementById("game-container").style.display = "none";
            document.getElementById("transition-container").style.display = "flex";
            document.getElementById("transition-story").innerText = gameStages[stageId].story;
            
            const nextBtn = document.getElementById("next-stage-btn");
            nextBtn.onclick = function() {
                startNextStage(gameStages[stageId].next);
            };
        } else {
            // 第7關：直接進結局
            document.getElementById("game-container").style.display = "none";
            document.getElementById("ending-container").style.display = "flex";
        }
    }

    function startNextStage(nextStageId) {
        currentStage = nextStageId;
        document.getElementById("transition-container").style.display = "none";
        document.getElementById("game-container").style.display = "flex";
        document.getElementById("stage-title").innerText = gameStages[currentStage].name;
    }

    function restartGame() {
        currentStage = 1;
        document.getElementById("ending-container").style.display = "none";
        document.getElementById("game-container").style.display = "flex";
        document.getElementById("stage-title").innerText = gameStages[currentStage].name;
    }
</script>
</body>
</html>
