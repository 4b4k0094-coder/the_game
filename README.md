<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>裡應外合</title>
    <style>
        /* 全局箱模型重設，防止尺寸爆開 */
        *, *::before, *::after {
            box-sizing: border-box;
        }

        /* 全局大明軍隊深夜海戰風格 */
        body {
            margin: 0;
            padding: 15px;
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
            width: 100%;
            max-width: 750px;
            padding: 10px;
            z-index: 20;
        }

        h1 {
            color: #eab308; 
            font-size: 2.3rem;
            letter-spacing: 4px;
            margin-top: 10px;
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
            text-align: left;
        }

        /* ⚔️ 遊戲觀測主舞台（手機電腦自動響應式等比例縮放） ⚔️ */
        .stage {
            position: relative;
            width: 95%;
            max-width: 850px;
            /* 💡 核心：鎖定 850:566 寬高比，不論何種螢幕都能完美縮放不變形 */
            aspect-ratio: 850 / 566; 
            background-image: url('底圖.png');
            background-size: 100% 100%;
            background-repeat: no-repeat;
            border: 3px solid #451a03;
            border-radius: 12px;
            box-shadow: inset 0 0 40px rgba(0,0,0,0.8), 0 12px 40px rgba(0,0,0,0.7);
            overflow: hidden;
            margin: 20px 0;
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

        /* 🎯 精準轉換為百分比座標，確保在手機小畫布上完美對齊 */
        #tower-0 {
            /* 左側大藍窗燈塔 */
            left: 9.41%;
            bottom: 19.43%;
            width: 18.24%;
            height: 54.77%;
            z-index: 3;
        }
        #tower-1 {
            /* 中間中型背景燈塔 */
            left: 32.35%;
            bottom: 44.17%;
            width: 11.18%;
            height: 38.87%;
            z-index: 3;
        }
        #tower-2 {
            /* 右上極遠處小型燈塔 */
            left: 62.35%;
            bottom: 58.30%;
            width: 7.65%;
            height: 26.50%;
            z-index: 3;
        }
        #tower-3 {
            /* 右下角特大前景燈塔 */
            left: 73.53%;
            bottom: 3.53%;
            width: 28.24%;
            height: 45.94%;
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
            width: 95%;
            max-width: 440px;
            z-index: 20;
            margin-bottom: 15px;
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

        /* 📱 手機移動端專用 RWD 覆蓋樣式 */
        @media (max-width: 600px) {
            body {
                padding: 10px;
            }
            h1 {
                font-size: 1.8rem;
                letter-spacing: 2px;
            }
            .story-text {
                font-size: 0.88rem;
                padding: 12px 18px;
                line-height: 1.6;
            }
            .stage {
                margin: 12px 0;
                border-width: 2px;
            }
            .terminal-box {
                padding: 18px 20px;
            }
            .terminal-title {
                font-size: 0.95rem;
                margin-bottom: 12px;
            }
            .code-input {
                width: 42px;
                height: 42px;
                font-size: 22px;
            }
            .submit-btn {
                padding: 10px 20px;
                font-size: 0.95rem;
            }
        }
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
            <input type="text" class="code-input" id="c1" maxlength="1" oninput="nextField(this, 'c2')" inputmode="numeric">
            <input type="text" class="code-input" id="c2" maxlength="1" oninput="nextField(this, 'c3')" inputmode="numeric">
            <input type="text" class="code-input" id="c3" maxlength="1" oninput="nextField(this, 'c4')" inputmode="numeric">
            <input type="text" class="code-input" id="c4" maxlength="1" oninput="nextField(this, null)" inputmode="numeric">
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
</body>
</html>
