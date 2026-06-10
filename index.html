<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>裡應外合</title>
    <style>
        /* 全局大明軍隊深夜海戰風格 */
        body {
            margin: 0;
            padding: 0;
            background: linear-gradient(to bottom, #050811, #121620);
            color: #f1f5f9;
            font-family: "Noto Serif TC", "Noto Sans TC", "Microsoft JhengHei", serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            overflow-x: hidden;
        }

        .header-container {
            text-align: center;
            max-width: 750px;
            padding: 20px;
            z-index: 20;
        }

        h1 {
            color: #eab308; 
            font-size: 2.3rem;
            letter-spacing: 4px;
            margin-bottom: 12px;
            text-shadow: 0 0 15px rgba(234, 179, 8, 0.3);
        }

        .story-text {
            color: #cbd5e1;
            font-size: 0.98rem;
            line-height: 1.7;
            background: rgba(20, 15, 10, 0.85);
            padding: 18px 25px;
            border-left: 4px solid #b91c1c; 
            border-radius: 4px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.5);
        }

        /* ⚔️ 遊戲觀測主舞台 ⚔️ */
        .stage {
            position: relative;
            width: 850px;
            height: 566px; 
            background-image: url('底圖.png');
            background-size: 100% 100%;
            background-repeat: no-repeat;
            border: 3px solid #451a03;
            border-radius: 12px;
            box-shadow: inset 0 0 40px rgba(0,0,0,0.8), 0 12px 40px rgba(0,0,0,0.7);
            overflow: hidden;
            margin: 25px 0;
        }

        /* 圖層 1：草地環境 */
        .grass-layer {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('草地.png');
            background-size: 100% 100%;
            pointer-events: none;
            z-index: 1;
        }

        /* 圖層 2：夜幕籠罩 */
        .night-layer {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('夜幕（透明.png');
            background-size: 100% 100%;
            pointer-events: none;
            z-index: 2;
        }

        /* ⚓ 圖層 3：動態烽火燈塔 */
        .tower {
            position: absolute;
            object-fit: cover;
            object-position: top; 
            display: block;
        }

        /* 精準控制位置與比例 */
        #tower-0 {
            /* 左側大藍窗燈塔 */
            left: 80px;
            bottom: 110px;
            width: 155px;
            height: 310px;
            z-index: 3;
        }
        #tower-1 {
            /* 中間中型背景燈塔 */
            left: 275px;
            bottom: 250px;
            width: 95px;
            height: 220px;
            z-index: 3;
        }
        #tower-2 {
            /* 右上極遠處小型燈塔 */
            left: 530px;
            bottom: 330px;
            width: 65px;
            height: 150px;
            z-index: 3;
        }
        #tower-3 {
            /* 右下角特大前景燈塔 */
            left: 625px;
            bottom: 20px; 
            width: 240px;
            height: 260px;
            z-index: 3; 
        }

        /* 🧱 圖層 4：前景紅磚城牆 */
        .wall-layer {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('城牆.png');
            background-size: 100% 100%;
            pointer-events: none;
            z-index: 4; 
        }


        /* 國姓爺中軍大帳操作終端 */
        .terminal-box {
            background: #1c130c; 
            border: 2px solid #b91c1c;
            border-top: 6px solid #eab308;
            padding: 25px 40px;
            border-radius: 6px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.6);
            text-align: center;
            width: 440px;
            z-index: 20;
        }

        .terminal-title {
            font-size: 1.05rem;
            color: #eab308;
            margin-bottom: 15px;
            font-weight: bold;
            letter-spacing: 2px;
        }

        .code-container {
            display: flex;
            gap: 12px;
            justify-content: center;
            margin-bottom: 20px;
        }

        .code-input {
            width: 48px;
            height: 48px;
            background: #2e1f13;
            border: 2px solid #78350f;
            border-radius: 4px;
            font-size: 26px;
            color: #fde047;
            text-align: center;
            font-weight: bold;
            outline: none;
            transition: all 0.2s;
        }

        .code-input:focus {
            border-color: #eab308;
            box-shadow: 0 0 10px rgba(234, 179, 8, 0.5);
            background: #1c130c;
        }

        .submit-btn {
            background: #b91c1c;
            color: #ffffff;
            border: none;
            padding: 12px 25px;
            font-size: 1rem;
            font-weight: bold;
            border-radius: 4px;
            cursor: pointer;
            letter-spacing: 2px;
            transition: background 0.2s;
            width: 100%;
            box-shadow: 0 4px 10px rgba(185, 28, 28, 0.4);
        }

        .submit-btn:hover {
            background: #991b1b;
            color: #fde047;
        }

        #result-log {
            margin-top: 18px;
            font-size: 0.95rem;
            min-height: 24px;
            line-height: 1.6;
            letter-spacing: 0.5px;
        }
        .text-success { color: #4ade80; text-shadow: 0 0 5px rgba(0,0,0,0.5); font-weight: bold; }
        .text-error { color: #f87171; }
    </style>
</head>
<body>

    <div class="header-container">
        <h1>裡應外合</h1>
        <div class="story-text">
            <strong>【大軍密令】</strong> 永曆十五年，國姓爺鄭成功率鐵人軍與數百戰船進攻臺灣。今夜，我軍戰船已銜枚疾進，密佈於鹿耳門外海。潛伏在荷蘭熱蘭遮城內的漢人內應，正冒死點燃敵軍防線哨塔，企圖以火光向我軍傳遞「起義總攻」之密碼。<br>
            請前線指揮官嚴密計數四座哨塔閃爍的規律（天命之年號），並於帥帳宣洩密碼，克期開戰！
        </div>
    </div>

    <div class="stage">
        <div class="grass-layer"></div>
        <div class="night-layer"></div>
        
        <img src="燈塔（暗.png" class="tower" id="tower-0" alt="烽火台">
        <img src="燈塔（暗.png" class="tower" id="tower-1" alt="烽火台">
        <img src="燈塔（暗.png" class="tower" id="tower-2" alt="烽火台">
        
        <div class="wall-layer"></div>
        
        <img src="燈塔（暗.png" class="tower" id="tower-3" alt="前景烽火台">
    </div>

    <div class="terminal-box">
        <div class="terminal-title">⚔️ 國姓爺中軍帥帳．大軍密令</div>
        <div class="code-container">
            <input type="text" class="code-input" id="c1" maxlength="1" oninput="nextField(this, 'c2')">
            <input type="text" class="code-input" id="c2" maxlength="1" oninput="nextField(this, 'c3')">
            <input type="text" class="code-input" id="c3" maxlength="1" oninput="nextField(this, 'c4')">
            <input type="text" class="code-input" id="c4" maxlength="1" oninput="nextField(this, null)">
        </div>
        <button class="submit-btn" onclick="checkCode()">發動總攻．收復臺灣</button>
        <div id="result-log"></div>
    </div>

    <script>
        const patterns = [1, 6, 6, 1]; 
        const lightOnTime = 500;     
        const lightOffTime = 420;    
        const transitionTime = 1800; 

        function nextField(current, nextInputId) {
            if (current.value.length >= 1 && nextInputId) {
                document.getElementById(nextInputId).focus();
            }
        }

        function startSignalLoop(towerIdx) {
            const maxFlashes = patterns[towerIdx];
            let currentFlashCount = 0;
            const towerEl = document.getElementById(`tower-${towerIdx}`);

            function flash() {
                if (currentFlashCount < maxFlashes) {
                    towerEl.src = '燈塔（亮.png'; 
                    
                    setTimeout(() => {
                        towerEl.src = '燈塔（暗.png'; 
                        currentFlashCount++;
                        setTimeout(flash, lightOffTime);
                    }, lightOnTime);
                } else {
                    setTimeout(() => {
                        const nextIdx = (towerIdx + 1) % 4;
                        startSignalLoop(nextIdx);
                    }, transitionTime);
                }
            }

            flash();
        }

        function checkCode() {
            const v1 = document.getElementById('c1').value;
            const v2 = document.getElementById('c2').value;
            const v3 = document.getElementById('c3').value;
            const v4 = document.getElementById('c4').value;
            
            const combinedCode = v1 + v2 + v3 + v4;
            const logEl = document.getElementById('result-log');

            if (combinedCode === '1661') {
                logEl.className = 'text-success';
                // 💡 調整：文字僅留「暗號正確！」及以前文字
                logEl.innerHTML = '🚩 【大軍聽令：開戰！】<br>暗號正確！';
            } else {
                logEl.className = 'text-error';
                logEl.innerHTML = '⚠️ 【軍情有誤．按兵不動】<br>暗號不符！海面風浪大作，恐是紅毛番的誘敵詭計。請重新嚴密審視哨塔火光次數！';
                
                setTimeout(() => {
                    document.getElementById('c1').value = '';
                    document.getElementById('c2').value = '';
                    document.getElementById('c3').value = '';
                    document.getElementById('c4').value = '';
                    document.getElementById('c1').focus();
                    logEl.innerText = '';
                }, 2500);
            }
        }

        window.onload = function() {
            startSignalLoop(0);
        };
    </script>
</body>
</html>
