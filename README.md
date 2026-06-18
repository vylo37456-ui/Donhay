<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tìm Độ Nhạy Free Fire Theo Dòng Máy</title>
    <style>
        * {
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
        }
        body {
            background-color: #121214;
            color: #e1e1e6;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }
        .container {
            background-color: #202024;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.5);
            width: 100%;
            max-width: 450px;
            border: 1px solid #ff4a4a;
        }
        h2 {
            text-align: center;
            color: #ff4a4a;
            margin-bottom: 20px;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-size: 20px;
        }
        .form-group {
            margin-bottom: 15px;
        }
        label {
            display: block;
            margin-bottom: 8px;
            font-size: 14px;
            color: #a8a8b3;
        }
        input[type="text"] {
            width: 100%;
            background-color: #121214;
            border: 1px solid #29292e;
            color: #fff;
            padding: 12px;
            border-radius: 5px;
            outline: none;
            font-size: 15px;
            transition: border 0.2s;
        }
        input[type="text"]:focus {
            border-color: #ff4a4a;
        }
        button {
            width: 100%;
            background-color: #ff4a4a;
            color: white;
            border: none;
            padding: 12px;
            border-radius: 5px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: background 0.2s;
            margin-top: 10px;
        }
        button:hover {
            background-color: #e03e3e;
        }
        .result {
            margin-top: 20px;
            background-color: #121214;
            padding: 15px;
            border-radius: 5px;
            border-left: 4px solid #ff4a4a;
            display: none;
        }
        .result h3 {
            font-size: 16px;
            margin-bottom: 10px;
            color: #fff;
        }
        .result p {
            font-size: 14px;
            margin: 6px 0;
            display: flex;
            justify-content: space-between;
        }
        .result span {
            color: #ff4a4a;
            font-weight: bold;
        }
        .note {
            margin-top: 10px;
            font-size: 12px;
            color: #a8a8b3;
            font-style: italic;
            line-height: 1.4;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Tra Độ Nhạy Free Fire</h2>
    
    <div class="form-group">
        <label for="deviceInput">Nhập tên dòng máy của bạn:</label>
        <input type="text" id="deviceInput" placeholder="Ví dụ: iPhone 11, Oppo A94, Redmi..." autocomplete="off">
    </div>

    <button onclick="searchSensitivity()">Tìm Độ Nhạy</button>

    <div class="result" id="resultBox">
        <h3 id="resultTitle">Độ nhạy gợi ý cho máy:</h3>
        <p>Nhìn xung quanh: <span id="r_general">0</span></p>
        <p>Red Dot Sight: <span id="r_reddot">0</span></p>
        <p>Ống ngắm 2x: <span id="r_x2">0</span></p>
        <p>Ống ngắm 4x: <span id="r_x4">0</span></p>
        <p>Ống ngắm AWM: <span id="r_awm">0</span></p>
        <p>Góc nhìn tự do: <span id="r_look">0</span></p>
        <p>Nút bắn khuyến nghị: <span id="r_button">0</span></p>
        <div class="note" id="r_note"></div>
    </div>
</div>

<script>
    function searchSensitivity() {
        const input = document.getElementById('deviceInput').value.trim().toLowerCase();
        if (!input) {
            alert('Vui lòng nhập tên dòng máy!');
            return;
        }

        let deviceName = document.getElementById('deviceInput').value;
        let sens = { general: 95, reddot: 90, x2: 85, x4: 80, awm: 50, look: 70, button: "45% - 50%", dpi: "Mặc định" };

        // Thuật toán tự động quét từ khóa để nhận diện mọi dòng máy
        if (input.includes('iphone') || input.includes('ipad') || input.includes('ios') || input.includes('ip')) {
            sens = { general: 98, reddot: 95, x2: 92, x4: 88, awm: 55, look: 80, button: "42%", dpi: "Mặc định (iOS vuốt siêu mượt)" };
        } else if (input.includes('samsung') || input.includes('ss')) {
            sens = { general: 100, reddot: 96, x2: 94, x4: 90, awm: 48, look: 75, button: "48%", dpi: "Tăng thêm +60 DPI so với gốc" };
        } else if (input.includes('oppo') || input.includes('realme')) {
            sens = { general: 96, reddot: 92, x2: 88, x4: 85, awm: 50, look: 70, button: "45%", dpi: "480 hoặc giữ mặc định" };
        } else if (input.includes('xiaomi') || input.includes('redmi') || input.includes('poco')) {
            sens = { general: 97, reddot: 94, x2: 90, x4: 86, awm: 52, look: 75, button: "47%", dpi: "500" };
        } else if (input.includes('vivo')) {
            sens = { general: 95, reddot: 90, x2: 88, x4: 84, awm: 45, look: 65, button: "50%", dpi: "Mặc định" };
        } else {
            // Cấu hình tối ưu thông minh dành cho các dòng máy lạ khác
            sens = { general: 98, reddot: 95, x2: 90, x4: 85, awm: 50, look: 70, button: "45% - 52%", dpi: "Tăng nhẹ 50 đơn vị nếu vuốt thấy nặng" };
        }

        // Hiển thị kết quả ra màn hình
        document.getElementById('resultTitle').textContent = "Độ nhạy tối ưu cho: " + deviceName;
        document.getElementById('r_general').textContent = sens.general;
        document.getElementById('r_reddot').textContent = sens.reddot;
        document.getElementById('r_x2').textContent = sens.x2;
        document.getElementById('r_x4').textContent = sens.x4;
        document.getElementById('r_awm').textContent = sens.awm;
        document.getElementById('r_look').textContent = sens.look;
        document.getElementById('r_button').textContent = sens.button;
        document.getElementById('r_note').innerHTML = "* Khuyến nghị DPI: <strong>" + sens.dpi + "</strong>. Đặt nút bắn thấp để có khoảng trống kéo tâm.";

        document.getElementById('resultBox').style.display = 'block';
    }
    
    // Hỗ trợ nhấn nút Enter để tìm kiếm luôn
    document.getElementById('deviceInput').addEventListener('keypress', function (e) {
        if (e.key === 'Enter') {
            searchSensitivity();
        }
    });
</script>

</body>
</html>
