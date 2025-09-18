[index.html](https://github.com/user-attachments/files/22397574/index.html)
<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <title>เกมขัดแยกขยะ</title>
  <style>
    body
      * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 30%, #80deea 70%, #4dd0e1 100%);
            min-height: 100vh;
            padding: 20px;
            text-align: center;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }
        
        .game-container {
            max-width: 900px;
            width: 100%;
            margin: 20px auto;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            padding: 25px;
            box-shadow: 0 10px 30px rgba(0, 150, 136, 0.2);
            backdrop-filter: blur(5px);
            border: 1px solid rgba(255, 255, 255, 0.5);
        }
        
        .header {
            margin-bottom: 25px;
            position: relative;
        }
        
        h1 {
            color: #00695c;
            margin-bottom: 15px;
            font-size: 2.8rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
            position: relative;
            display: inline-block;
        }
        
        h1:after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 4px;
            background: linear-gradient(90deg, #4db6ac, #00796b);
            border-radius: 2px;
        }
        
        .instructions {
            background: linear-gradient(135deg, #e8f5e9, #c8e6c9);
            padding: 15px;
            border-radius: 12px;
            margin-bottom: 20px;
            border-left: 5px solid #388e3c;
            text-align: left;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
        }
        
        .instructions h3 {
            color: #2e7d32;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .instructions ul {
            list-style-type: none;
            padding-left: 10px;
        }
        
        .instructions li {
            margin-bottom: 8px;
            display: flex;
            align-items: center;
            gap: 8px;
            color: #424242;
        }
        
        .instructions i {
            color: #388e3c;
            font-size: 1.2rem;
        }
        
        .info-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
            flex-wrap: wrap;
            gap: 15px;
        }
        
        .score-board {
            font-size: 1.3rem;
            color: #37474f;
            background: linear-gradient(135deg, #bbdefb, #90caf9);
            padding: 12px 20px;
            border-radius: 50px;
            display: inline-block;
            box-shadow: 0 4px 8px rgba(33, 150, 243, 0.2);
            flex: 1;
        }
        
        .timer-container {
            font-size: 1.3rem;
            color: #37474f;
            background: linear-gradient(135deg, #fff9c4, #fff176);
            padding: 12px 20px;
            border-radius: 50px;
            display: inline-block;
            box-shadow: 0 4px 8px rgba(255, 193, 7, 0.2);
            flex: 1;
        }
        
        .timer-container.warning {
            background: linear-gradient(135deg, #ffcdd2, #ef9a9a);
            color: #c62828;
            animation: pulse 1s infinite;
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        .round-info {
            font-size: 1.3rem;
            color: #37474f;
            background: linear-gradient(135deg, #d1c4e9, #b39ddb);
            padding: 12px 20px;
            border-radius: 50px;
            display: inline-block;
            box-shadow: 0 4px 8px rgba(103, 58, 183, 0.2);
            flex: 1;
        }
        
        .bins-container {
            display: flex;
            justify-content: space-around;
            margin-bottom: 35px;
            flex-wrap: wrap;
            gap: 15px;
        }
        
        .bin {
            width: 160px;
            height: 220px;
            margin: 10px;
            border-radius: 15px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-end;
            position: relative;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
            overflow: hidden;
        }
        
        .bin:before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 15px;
            background: rgba(255, 255, 255, 0.5);
            border-bottom: 2px solid rgba(255, 255, 255, 0.3);
        }
        
        .bin-top {
            width: 100%;
            height: 35px;
            border-top-left-radius: 15px;
            border-top-right-radius: 15px;
            position: relative;
            z-index: 2;
        }
        
        .bin-body {
            width: 90%;
            height: 185px;
            border-bottom-left-radius: 15px;
            border-bottom-right-radius: 15px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.4);
            position: relative;
            z-index: 1;
            padding: 10px;
        }
        
        .bin-type {
            font-size: 1.1rem;
            margin-bottom: 5px;
        }
        
        .bin-examples {
            font-size: 0.85rem;
            font-weight: normal;
            opacity: 0.9;
            margin-top: 8px;
        }
        
        .blue-bin .bin-top { background: linear-gradient(135deg, #64b5f6, #1976d2); }
        .blue-bin .bin-body { background: linear-gradient(135deg, #42a5f5, #1565c0); }
        
        .green-bin .bin-top { background: linear-gradient(135deg, #81c784, #388e3c); }
        .green-bin .bin-body { background: linear-gradient(135deg, #66bb6a, #2e7d32); }
        
        .yellow-bin .bin-top { background: linear-gradient(135deg, #fff176, #fbc02d); }
        .yellow-bin .bin-body { background: linear-gradient(135deg, #ffee58, #f9a825); }
        
        .red-bin .bin-top { background: linear-gradient(135deg, #ff8a65, #d84315); }
        .red-bin .bin-body { background: linear-gradient(135deg, #ff7043, #bf360c); }
        
        .bin.incorrect {
            animation: shake 0.5s;
            box-shadow: 0 0 15px rgba(255, 0, 0, 0.5);
        }
        
        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            20%, 60% { transform: translateX(-8px); }
            40%, 80% { transform: translateX(8px); }
        }
        
        .trash-items {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            margin-bottom: 35px;
            padding: 15px;
            background: rgba(236, 239, 241, 0.5);
            border-radius: 15px;
            min-height: 180px;
        }
        
        .trash-item {
            width: 85px;
            height: 85px;
            border-radius: 12px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            cursor: grab;
            font-size: 2.8rem;
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            background: white;
            position: relative;
            overflow: hidden;
            animation: appear 0.5s ease;
        }
        
        @keyframes appear {
            from { transform: scale(0); opacity: 0; }
            to { transform: scale(1); opacity: 1; }
        }
        
        .trash-item:after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(135deg, rgba(255, 255, 255, 0.3), transparent);
            border-radius: 12px;
        }
        
        .trash-item:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.15);
        }
        
        .trash-name {
            position: absolute;
            bottom: -25px;
            left: 0;
            right: 0;
            font-size: 0.75rem;
            color: #37474f;
            font-weight: 500;
            opacity: 0;
            transition: opacity 0.3s;
        }
        
        .trash-item:hover .trash-name {
            opacity: 1;
        }
        
        .controls {
            margin-top: 25px;
            display: flex;
            justify-content: center;
            gap: 15px;
        }
        
        button {
            padding: 14px 30px;
            background: linear-gradient(135deg, #00acc1, #00838f);
            color: white;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-size: 1.1rem;
            font-weight: bold;
            transition: all 0.3s;
            box-shadow: 0 5px 15px rgba(0, 131, 143, 0.4);
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        button:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0, 131, 143, 0.6);
        }
        
        button:active {
            transform: translateY(1px);
        }
        
        .message {
            margin-top: 25px;
            padding: 20px;
            border-radius: 15px;
            font-weight: bold;
            display: none;
            animation: fadeIn 0.5s;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .success {
            background: linear-gradient(135deg, #c8e6c9, #a5d6a7);
            color: #2e7d32;
            display: none;
            border-left: 5px solid #4caf50;
        }
        
        .timeup {
            background: linear-gradient(135deg, #ffcdd2, #ef9a9a);
            color: #c62828;
            display: none;
            border-left: 5px solid #d32f2f;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .footer {
            margin-top: 30px;
            color: #546e7a;
            font-size: 0.9rem;
        }
        
        @media (max-width: 768px) {
            .bin {
                width: 130px;
                height: 190px;
            }
            
            .trash-item {
                width: 70px;
                height: 70px;
                font-size: 2.2rem;
            }
            
            h1 {
                font-size: 2.2rem;
            }
            
            .controls {
                flex-direction: column;
                align-items: center;
            }
            
            button {
                width: 100%;
                max-width: 300px;
                justify-content: center;
            }
            
            .info-container {
                flex-direction: column;
            }
        }
        
        @media (max-width: 480px) {
            .bins-container {
                gap: 10px;
            }
            
            .bin {
                width: 45%;
                height: 180px;
                margin: 5px;
            }
            
            .trash-items {
                gap: 12px;
            }
            
            .trash-item {
                width: 60px;
                height: 60px;
                font-size: 1.8rem;
            }
            
            .bin-type {
                font-size: 1rem;
            }
            
            .bin-examples {
                font-size: 0.7rem;
            }
        }
    </style>
</head>
<body>
    <div class="game-container">
        <div class="header">
            <h1><i class="fas fa-recycle"></i> เกมขัดแยกขยะ</h1>
            
            <div class="instructions">
                <h3><i class="fas fa-info-circle"></i> วิธีเล่น</h3>
                <ul>
                    <li><i class="fas fa-check-circle"></i> ลากขยะแต่ละชิ้นไปวางบนถังขยะที่คิดว่าถูกต้อง</li>
                    <li><i class="fas fa-check-circle"></i> แยกขยะทั้งหมด 12 ชิ้นให้ถูกต้องภายใน 2 นาที</li>
                    <li><i class="fas fa-check-circle"></i> ถังขยะจะสั่นและแสดงสีแดงหากแยกผิด</li>
                    <li><i class="fas fa-check-circle"></i> ขยะจะเปลี่ยนไปทุกครั้งที่เริ่มเกมใหม่</li>
                </ul>
            </div>
        </div>
        
        <div class="info-container">
            <div class="score-board">
                <p>ขยะที่แยกแล้ว: <span id="trash-count">0</span> / 12</p>
            </div>
            
            <div class="timer-container" id="timer">
                <p>เวลาเหลือ: <span id="minutes">02</span>:<span id="seconds">00</span></p>
            </div>
            
            <div class="round-info">
                <p>รอบที่: <span id="round-number">1</span></p>
            </div>
        </div>
        
        <div class="bins-container">
            <div class="bin blue-bin" data-type="recyclable">
                <div class="bin-top"></div>
                <div class="bin-body">
                    <div class="bin-type">ขยะรีไซเคิล</div>
                    <div class="bin-examples">(กระดาษ, ขวดพลาสติก, กระป๋อง)</div>
                </div>
            </div>
            
            <div class="bin green-bin" data-type="organic">
                <div class="bin-top"></div>
                <div class="bin-body">
                    <div class="bin-type">ขยะอินทรีย์</div>
                    <div class="bin-examples">(เปลือกผลไม้, เศษอาหาร, ใบไม้)</div>
                </div>
            </div>
            
            <div class="bin yellow-bin" data-type="general">
                <div class="bin-top"></div>
                <div class="bin-body">
                    <div class="bin-type">ขยะทั่วไป</div>
                    <div class="bin-examples">(ถุงพลาสติก, ฟอยล์อาหาร, หลอด)</div>
                </div>
            </div>
            
            <div class="bin red-bin" data-type="hazardous">
                <div class="bin-top"></div>
                <div class="bin-body">
                    <div class="bin-type">ขยะอันตราย</div>
                    <div class="bin-examples">(หลอดไฟ, แบตเตอรี่, สารเคมี)</div>
                </div>
            </div>
        </div>
        
        <div class="trash-items" id="trash-items">
            <!-- ขยะจะถูกเพิ่มโดย JavaScript -->
        </div>
        
        <div class="controls">
            <button id="restart-btn"><i class="fas fa-redo"></i> เริ่มเกมใหม่</button>
            <button id="next-round-btn"><i class="fas fa-forward"></i> รอบถัดไป</button>
        </div>
        
        <div class="message success" id="success-message">
            <i class="fas fa-trophy"></i> ยินดีด้วย! คุณแยกขยะถูกต้องทั้งหมด กำลังเริ่มรอบใหม่...
        </div>
        
        <div class="message timeup" id="timeup-message">
            <i class="fas fa-clock"></i> เวลาหมดแล้ว! กดเริ่มเกมใหม่เพื่อเล่นอีกครั้ง
        </div>
    </div>

    <div class="footer">
        <p>สร้างด้วย HTML, CSS และ JavaScript | เกมเพื่อสิ่งแวดล้อม</p>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // ข้อมูลขยะและประเภท (มีขยะเพิ่มมากขึ้นเพื่อสุ่มเลือก)
            const allTrashItems = [
                // ขยะรีไซเคิล
                { name: "กระดาษ", type: "recyclable", emoji: "📄" },
                { name: "ขวดพลาสติก", type: "recyclable", emoji: "🧴" },
                { name: "กระป๋องอลูมิเนียม", type: "recyclable", emoji: "🥫" },
                { name: "ขวดแก้ว", type: "recyclable", emoji: "🍶" },
                { name: "หนังสือ", type: "recyclable", emoji: "📚" },
                { name: "กล่องกระดาษ", type: "recyclable", emoji: "📦" },
                { name: "นิตยสาร", type: "recyclable", emoji: "📰" },
                { name: "กล่องนม", type: "recyclable", emoji: "🥛" },
                
                // ขยะอินทรีย์
                { name: "เปลือกผลไม้", type: "organic", emoji: "🍌" },
                { name: "เศษอาหาร", type: "organic", emoji: "🍲" },
                { name: "ใบไม้", type: "organic", emoji: "🍃" },
                { name: "เปลือกไข่", type: "organic", emoji: "🥚" },
                { name: "กากกาแฟ", type: "organic", emoji: "☕" },
                { name: "เปลือกถั่ว", type: "organic", emoji: "🥜" },
                { name: "เศษพืช", type: "organic", emoji: "🌿" },
                { name: "อาหารเหลือ", type: "organic", emoji: "🍛" },
                
                // ขยะทั่วไป
                { name: "ถุงพลาสติก", type: "general", emoji: "🛍️" },
                { name: "ฟอยล์อาหาร", type: "general", emoji: "🥡" },
                { name: "หลอด", type: "general", emoji: "🥤" },
                { name: "ภาชนะโฟม", type: "general", emoji: "🍱" },
                { name: "ทิชชู่", type: "general", emoji: "🧻" },
                { name: "แผ่นCD", type: "general", emoji: "💿" },
                { name: "แปรงสีฟัน", type: "general", emoji: "🪥" },
                { name: "ไม้พันสำลี", type: "general", emoji: "🪥" },
                
                // ขยะอันตราย
                { name: "หลอดไฟ", type: "hazardous", emoji: "💡" },
                { name: "แบตเตอรี่", type: "hazardous", emoji: "🔋" },
                { name: "สารเคมี", type: "hazardous", emoji: "🧪" },
                { name: "ยาหมดอายุ", type: "hazardous", emoji: "💊" },
                { name: "เทอร์โมมิเตอร์", type: "hazardous", emoji: "🌡️" },
                { name: "กระป๋องสเปรย์", type: "hazardous", emoji: "🧴" },
                { name: "สีทาบ้าน", type: "hazardous", emoji: "🎨" },
                { name: "อุปกรณ์อิเล็กทรอนิกส์", type: "hazardous", emoji: "📱" }
            ];
            
            const bins = document.querySelectorAll('.bin');
            const trashContainer = document.getElementById('trash-items');
            const restartBtn = document.getElementById('restart-btn');
            const nextRoundBtn = document.getElementById('next-round-btn');
            const trashCountElement = document.getElementById('trash-count');
            const roundNumberElement = document.getElementById('round-number');
            const successMessage = document.getElementById('success-message');
            const timeupMessage = document.getElementById('timeup-message');
            const timerContainer = document.getElementById('timer');
            const minutesElement = document.getElementById('minutes');
            const secondsElement = document.getElementById('seconds');
            
            let correctCount = 0;
            let currentTrashItems = [];
            let roundNumber = 1;
            let timer;
            let timeLeft = 120; // 2 นาทีในหน่วยวินาที
            
            // ฟังก์ชันสุ่มเลือกขยะ 12 ชิ้นจากทั้งหมด
            function getRandomTrashItems() {
                const shuffled = [...allTrashItems].sort(() => 0.5 - Math.random());
                return shuffled.slice(0, 12);
            }
            
            // เริ่มจับเวลา
            function startTimer() {
                clearInterval(timer);
                timeLeft = 120;
                updateTimerDisplay();
                
                timer = setInterval(function() {
                    timeLeft--;
                    updateTimerDisplay();
                    
                    if (timeLeft <= 0) {
                        clearInterval(timer);
                        timeUp();
                    } else if (timeLeft <= 30) {
                        timerContainer.classList.add('warning');
                    }
                }, 1000);
            }
            
            // อัพเดทการแสดงผลเวลา
            function updateTimerDisplay() {
                const minutes = Math.floor(timeLeft / 60);
                const seconds = timeLeft % 60;
                
                minutesElement.textContent = minutes.toString().padStart(2, '0');
                secondsElement.textContent = seconds.toString().padStart(2, '0');
            }
            
            // เวลาหมด
            function timeUp() {
                timeupMessage.style.display = 'block';
                // ปิดการลากขยะ
                const trashItems = document.querySelectorAll('.trash-item');
                trashItems.forEach(item => {
                    item.draggable = false;
                    item.style.cursor = 'not-allowed';
                    item.style.opacity = '0.7';
                });
            }
            
            // เริ่มเกม
            function startGame() {
                // ล้างข้อมูลเกมก่อนหน้า
                correctCount = 0;
                trashCountElement.textContent = '0';
                trashContainer.innerHTML = '';
                successMessage.style.display = 'none';
                timeupMessage.style.display = 'none';
                timerContainer.classList.remove('warning');
                
                // เริ่มจับเวลา
                startTimer();
                
                // สุ่มเลือกขยะ 12 ชิ้น
                currentTrashItems = getRandomTrashItems();
                
                // สร้างองค์ประกอบขยะ
                currentTrashItems.forEach((trash, index) => {
                    const trashElement = document.createElement('div');
                    trashElement.className = 'trash-item';
                    trashElement.draggable = true;
                    trashElement.dataset.type = trash.type;
                    trashElement.dataset.index = index;
                    trashElement.innerHTML = `${trash.emoji}<div class="trash-name">${trash.name}</div>`;
                    
                    // เพิ่มการจัดการการลากและวาง
                    trashElement.addEventListener('dragstart', dragStart);
                    
                    trashContainer.appendChild(trashElement);
                });
            }
            
            // เริ่มรอบใหม่
            function nextRound() {
                roundNumber++;
                roundNumberElement.textContent = roundNumber;
                startGame();
            }
            
            // การจัดการการลากเริ่มต้น
            function dragStart(e) {
                e.dataTransfer.setData('text/plain', e.target.dataset.index);
            }
            
            // การจัดการการวาง
            function dragOver(e) {
                e.preventDefault();
            }
            
            function drop(e) {
                e.preventDefault();
                const trashIndex = e.dataTransfer.getData('text/plain');
                const trashElement = document.querySelector(`.trash-item[data-index="${trashIndex}"]`);
                if (!trashElement) return;
                
                const trashType = trashElement.dataset.type;
                const binType = this.dataset.type;
                
                // ตรวจสอบว่าถูกต้องหรือไม่
                if (trashType === binType) {
                    // ถูกต้อง - ลบขยะออก
                    trashElement.style.transform = 'scale(0)';
                    trashElement.style.opacity = '0';
                    setTimeout(() => {
                        trashElement.remove();
                    }, 300);
                    
                    correctCount++;
                    trashCountElement.textContent = correctCount;
                    
                    // ตรวจสอบว่าเกมจบแล้วหรือยัง
                    if (correctCount === 12) {
                        clearInterval(timer);
                        successMessage.style.display = 'block';
                        setTimeout(() => {
                            nextRound();
                        }, 2000);
                    }
                } else {
                    // ไม่ถูกต้อง - แสดงแอนิเมชั่น
                    this.classList.add('incorrect');
                    setTimeout(() => {
                        this.classList.remove('incorrect');
                    }, 500);
                }
            }
            
            // เพิ่มการจัดการการวางให้กับถังขยะแต่ละใบ
            bins.forEach(bin => {
                bin.addEventListener('dragover', dragOver);
                bin.addEventListener('drop', drop);
            });
            
            // การจัดการปุ่มเริ่มใหม่
            restartBtn.addEventListener('click', function() {
                roundNumber = 1;
                roundNumberElement.textContent = roundNumber;
                startGame();
            });
            
            // การจัดการปุ่มรอบถัดไป
            nextRoundBtn.addEventListener('click', nextRound);
            
            // เริ่มเกม
            startGame();
        });
    </script>

  <script>
    function allowDrop(event) {
      event.preventDefault();
    }
    document.querySelectorAll('.trash').forEach(item => {
      item.addEventListener('dragstart', ev => {
        ev.dataTransfer.setData("text", ev.target.textContent);
      });
    });
    function drop(ev, binType) {
      ev.preventDefault();
      const data = ev.dataTransfer.getData("text");
      alert("คุณทิ้ง " + data + " ลงถัง " + binType + " !");
    }
  </script>
</body>
</html>
