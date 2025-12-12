<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Máy Tính BMI - Công Cụ Sức Khỏe</title>
    <style>
        /* CSS tích hợp */
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f0f2f5;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
        }

        .container {
            background-color: #ffffff;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
            width: 100%;
            max-width: 400px;
            text-align: center;
        }

        h1 {
            color: #1a73e8;
            margin-bottom: 20px;
            font-size: 24px;
        }

        .input-group {
            text-align: left;
            margin-bottom: 20px;
        }

        .input-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #444;
        }

        .input-group input {
            width: 100%;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            box-sizing: border-box;
            font-size: 16px;
            transition: border-color 0.3s;
        }

        .input-group input:focus {
            border-color: #1a73e8;
            outline: none;
        }

        button {
            background-color: #1a73e8;
            color: white;
            padding: 14px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 18px;
            font-weight: bold;
            width: 100%;
            transition: background-color 0.3s;
        }

        button:hover {
            background-color: #1557b0;
        }

        .result-box {
            margin-top: 25px;
            padding: 20px;
            border-radius: 8px;
            background-color: #f8f9fa;
            display: none; /* Ẩn khi chưa tính */
        }

        .bmi-score {
            font-size: 32px;
            font-weight: bold;
            color: #1a73e8;
            margin: 10px 0;
        }

        .bmi-status {
            font-size: 18px;
            font-weight: 600;
        }

        .info-table {
            margin-top: 25px;
            width: 100%;
            border-collapse: collapse;
            font-size: 14px;
        }

        .info-table th, .info-table td {
            padding: 10px;
            border-bottom: 1px solid #eee;
            text-align: left;
        }

        .info-table th {
            background-color: #f8f9fa;
            color: #666;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Tính Chỉ Số BMI</h1>
        
        <div class="input-group">
            <label for="height">Chiều cao (cm):</label>
            <input type="number" id="height" placeholder="Ví dụ: 170" step="0.1">
        </div>
        
        <div class="input-group">
            <label for="weight">Cân nặng (kg):</label>
            <input type="number" id="weight" placeholder="Ví dụ: 65" step="0.1">
        </div>
        
        <button onclick="calculateBMI()">Tính ngay</button>

        <div id="resultBox" class="result-box">
            <div>Chỉ số BMI của bạn là:</div>
            <div id="bmiScore" class="bmi-score">22.5</div>
            <div id="bmiStatus" class="bmi-status">Bình thường</div>
        </div>

        <table class="info-table">
            <thead>
                <tr>
                    <th>BMI</th>
                    <th>Phân loại (WHO)</th>
                </tr>
            </thead>
            <tbody>
                <tr><td>Dưới 18.5</td><td>Thiếu cân</td></tr>
                <tr><td>18.5 - 24.9</td><td>Bình thường</td></tr>
                <tr><td>25.0 - 29.9</td><td>Thừa cân</td></tr>
                <tr><td>Trên 30.0</td><td>Béo phì</td></tr>
            </tbody>
        </table>
    </div>

    <script>
        // JavaScript tích hợp
        function calculateBMI() {
            const height = document.getElementById('height').value;
            const weight = document.getElementById('weight').value;
            const resultBox = document.getElementById('resultBox');
            const bmiScore = document.getElementById('bmiScore');
            const bmiStatus = document.getElementById('bmiStatus');

            if (height > 0 && weight > 0) {
                // Công thức: BMI = Cân nặng (kg) / (Chiều cao (m) ^ 2)
                const heightInMeters = height / 100;
                const bmi = (weight / (heightInMeters * heightInMeters)).toFixed(1);
                
                // Hiển thị kết quả
                bmiScore.innerHTML = bmi;
                resultBox.style.display = 'block';

                // Phân loại
                if (bmi < 18.5) {
                    bmiStatus.innerHTML = "Thiếu cân";
                    bmiStatus.style.color = "#f39c12";
                } else if (bmi >= 18.5 && bmi <= 24.9) {
                    bmiStatus.innerHTML = "Bình thường";
                    bmiStatus.style.color = "#27ae60";
                } else if (bmi >= 25 && bmi <= 29.9) {
                    bmiStatus.innerHTML = "Thừa cân";
                    bmiStatus.style.color = "#e67e22";
                } else {
                    bmiStatus.innerHTML = "Béo phì";
                    bmiStatus.style.color = "#c0392b";
                }
            } else {
                alert("Vui lòng nhập chiều cao và cân nặng hợp lệ!");
            }
        }
    </script>

</body>
</html>
