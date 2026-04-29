# Sportsbook
Uy tin, co dien
<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Nghiên cứu tỉ lệ thắng - Manchester City</title>
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
        font-family: 'Segoe UI', Tahoma, sans-serif;
        background: linear-gradient(135deg, #f0f9ff 0%, #e0f2fe 100%);
        color: #1e293b;
        line-height: 1.6;
    }
    header {
        background: linear-gradient(135deg, #6CABDD 0%, #1C2C5B 100%);
        color: white;
        padding: 60px 20px;
        text-align: center;
        box-shadow: 0 4px 20px rgba(0,0,0,0.15);
    }
    header h1 {
        font-size: 2.8em;
        margin-bottom: 10px;
        text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
    }
    header p {
        font-size: 1.2em;
        opacity: 0.95;
    }
    .badge {
        display: inline-block;
        background: rgba(255,255,255,0.2);
        padding: 8px 20px;
        border-radius: 20px;
        margin-top: 15px;
        backdrop-filter: blur(10px);
    }
    .container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 40px 20px;
    }
    .section {
        background: white;
        border-radius: 16px;
        padding: 35px;
        margin-bottom: 30px;
        box-shadow: 0 4px 20px rgba(0,0,0,0.08);
        border-top: 4px solid #6CABDD;
    }
    .section h2 {
        color: #1C2C5B;
        margin-bottom: 20px;
        font-size: 1.8em;
        border-bottom: 2px solid #e0f2fe;
        padding-bottom: 10px;
    }
    .section h3 {
        color: #1C2C5B;
        margin: 20px 0 12px;
        font-size: 1.3em;
    }
    .section p {
        margin-bottom: 12px;
        text-align: justify;
    }
    .stats-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
        gap: 20px;
        margin: 25px 0;
    }
    .stat-card {
        background: linear-gradient(135deg, #6CABDD 0%, #4a90c2 100%);
        color: white;
        padding: 25px;
        border-radius: 12px;
        text-align: center;
        transition: transform 0.3s;
        box-shadow: 0 4px 15px rgba(108,171,221,0.3);
    }
    .stat-card:hover {
        transform: translateY(-5px);
    }
    .stat-card .number {
        font-size: 2.5em;
        font-weight: bold;
        margin-bottom: 5px;
    }
    .stat-card .label {
        font-size: 0.95em;
        opacity: 0.95;
    }
    table {
        width: 100%;
        border-collapse: collapse;
        margin: 20px 0;
        background: white;
        border-radius: 8px;
        overflow: hidden;
        box-shadow: 0 2px 8px rgba(0,0,0,0.05);
    }
    th {
        background: #1C2C5B;
        color: white;
        padding: 14px 12px;
        text-align: left;
        font-weight: 600;
    }
    td {
        padding: 12px;
        border-bottom: 1px solid #e0f2fe;
    }
    tr:hover {
        background: #f0f9ff;
    }
    tr:last-child td { border-bottom: none; }
    .chart-container {
        position: relative;
        height: 400px;
        margin: 25px 0;
    }
    .highlight {
        background: linear-gradient(120deg, #fef3c7 0%, #fde68a 100%);
        padding: 18px;
        border-radius: 10px;
        border-left: 4px solid #f59e0b;
        margin: 15px 0;
    }
    .source {
        font-size: 0.85em;
        color: #64748b;
        margin-top: 20px;
        padding-top: 15px;
        border-top: 1px dashed #cbd5e1;
        font-style: italic;
    }
    footer {
        background: #1C2C5B;
        color: white;
        text-align: center;
        padding: 30px 20px;
        margin-top: 40px;
    }
    footer p { opacity: 0.85; }
    .pct-bar {
        background: #e0f2fe;
        border-radius: 8px;
        overflow: hidden;
        height: 28px;
        margin: 8px 0;
        position: relative;
    }
    .pct-fill {
        background: linear-gradient(90deg, #6CABDD, #1C2C5B);
        height: 100%;
        color: white;
        display: flex;
        align-items: center;
        padding-left: 12px;
        font-weight: 600;
        font-size: 0.9em;
        transition: width 1s ease;
    }
    .competition-row {
        display: grid;
        grid-template-columns: 200px 1fr 80px;
        gap: 12px;
        align-items: center;
        margin: 12px 0;
    }
    .competition-row .name { font-weight: 600; color: #1C2C5B; }
    .competition-row .pct { text-align: right; font-weight: 600; color: #6CABDD; }
    @media (max-width: 768px) {
        header h1 { font-size: 2em; }
        .competition-row { grid-template-columns: 130px 1fr 60px; font-size: 0.9em; }
    }
</style>
</head>
<body>

<header>
    <h1>⚽ Nghiên cứu tỉ lệ thắng của Manchester City</h1>
    <p>Phân tích thống kê hiệu suất thi đấu của câu lạc bộ Manchester City F.C.</p>
    <div class="badge">Dữ liệu cập nhật đến mùa giải 2024/25</div>
</header>

<div class="container">

    <div class="section">
        <h2>1. Tổng quan về Manchester City</h2>
        <p>Manchester City Football Club (thường gọi là Man City) là câu lạc bộ bóng đá chuyên nghiệp có trụ sở tại Manchester, Anh. Được thành lập năm 1880, đội bóng hiện thi đấu tại Premier League và là một trong những câu lạc bộ thành công nhất nước Anh trong thập kỷ qua.</p>
        <p>Dưới triều đại HLV Pep Guardiola (từ 2016), Man City đã trở thành "cỗ máy chiến thắng" với phong cách kiểm soát bóng (tiki-taka cải tiến) và tỉ lệ thắng cao kỷ lục trong lịch sử bóng đá Anh.</p>

        <div class="stats-grid">
            <div class="stat-card">
                <div class="number">~73%</div>
                <div class="label">Tỉ lệ thắng dưới thời Pep Guardiola</div>
            </div>
            <div class="stat-card">
                <div class="number">8</div>
                <div class="label">Chức vô địch Premier League</div>
            </div>
            <div class="stat-card">
                <div class="number">1</div>
                <div class="label">Champions League (2022/23)</div>
            </div>
            <div class="stat-card">
                <div class="number">100</div>
                <div class="label">Điểm kỷ lục Premier League (2017/18)</div>
            </div>
        </div>
    </div>

    <div class="section">
        <h2>2. Tỉ lệ thắng theo mùa giải (Tất cả các đấu trường)</h2>
        <p>Bảng dưới đây tổng hợp tỉ lệ thắng của Manchester City qua các mùa giải gần đây trên tất cả các đấu trường (Premier League, FA Cup, EFL Cup, Champions League, FIFA Club World Cup...).</p>

        <div class="chart-container">
            <canvas id="seasonChart"></canvas>
        </div>

        <table>
            <thead>
                <tr>
                    <th>Mùa giải</th>
                    <th>Trận</th>
                    <th>Thắng</th>
                    <th>Hòa</th>
                    <th>Thua</th>
                    <th>Tỉ lệ thắng</th>
                    <th>Thành tích nổi bật</th>
                </tr>
            </thead>
            <tbody>
                <tr><td>2017/18</td><td>54</td><td>41</td><td>7</td><td>6</td><td><b>75.9%</b></td><td>Vô địch PL với 100 điểm</td></tr>
                <tr><td>2018/19</td><td>61</td><td>50</td><td>4</td><td>7</td><td><b>82.0%</b></td><td>Cú ăn ba quốc nội</td></tr>
                <tr><td>2019/20</td><td>61</td><td>40</td><td>9</td><td>12</td><td><b>65.6%</b></td><td>Á quân PL</td></tr>
                <tr><td>2020/21</td><td>61</td><td>42</td><td>10</td><td>9</td><td><b>68.9%</b></td><td>Vô địch PL, Á quân UCL</td></tr>
                <tr><td>2021/22</td><td>56</td><td>39</td><td>10</td><td>7</td><td><b>69.6%</b></td><td>Vô địch PL</td></tr>
                <tr><td>2022/23</td><td>61</td><td>45</td><td>6</td><td>10</td><td><b>73.8%</b></td><td>Cú ăn ba lịch sử (PL, FA, UCL)</td></tr>
                <tr><td>2023/24</td><td>59</td><td>40</td><td>13</td><td>6</td><td><b>67.8%</b></td><td>Vô địch PL lần thứ 4 liên tiếp</td></tr>
            </tbody>
        </table>

        <div class="highlight">
            <strong>Phát hiện quan trọng:</strong> Mùa giải 2018/19 là mùa giải có tỉ lệ thắng cao nhất với <b>82%</b>, khi Man City giành cú ăn ba quốc nội (Premier League, FA Cup, EFL Cup) - thành tích chưa từng có trong bóng đá Anh.
        </div>
    </div>

    <div class="section">
        <h2>3. Tỉ lệ thắng theo từng giải đấu</h2>
        <p>So sánh tỉ lệ thắng của Manchester City tại các đấu trường khác nhau dưới thời Pep Guardiola (2016-2024):</p>

        <div class="competition-row">
            <span class="name">Premier League</span>
            <div class="pct-bar"><div class="pct-fill" style="width: 75%">75.0%</div></div>
            <span class="pct">75%</span>
        </div>
        <div class="competition-row">
            <span class="name">FA Cup</span>
            <div class="pct-bar"><div class="pct-fill" style="width: 78%">77.5%</div></div>
            <span class="pct">77.5%</span>
        </div>
        <div class="competition-row">
            <span class="name">EFL Cup</span>
            <div class="pct-bar"><div class="pct-fill" style="width: 80%">80.0%</div></div>
            <span class="pct">80%</span>
        </div>
        <div class="competition-row">
            <span class="name">Champions League</span>
            <div class="pct-bar"><div class="pct-fill" style="width: 64%">64.2%</div></div>
            <span class="pct">64.2%</span>
        </div>
        <div class="competition-row">
            <span class="name">Sân nhà (Etihad)</span>
            <div class="pct-bar"><div class="pct-fill" style="width: 82%">81.8%</div></div>
            <span class="pct">81.8%</span>
        </div>
        <div class="competition-row">
            <span class="name">Sân khách</span>
            <div class="pct-bar"><div class="pct-fill" style="width: 65%">65.3%</div></div>
            <span class="pct">65.3%</span>
        </div>

        <h3>Phân tích:</h3>
        <p>Man City có tỉ lệ thắng cao nhất tại các giải đấu cúp quốc nội (FA Cup, EFL Cup) do thường gặp đối thủ yếu hơn ở vòng đầu. Tại Champions League, tỉ lệ thắng thấp hơn vì gặp các đối thủ mạnh nhất châu Âu, nhưng đã cải thiện đáng kể từ khi vô địch năm 2023.</p>
    </div>

    <div class="section">
        <h2>4. So sánh kỷ nguyên: Trước và dưới thời Pep Guardiola</h2>
        <div class="chart-container">
            <canvas id="comparisonChart"></canvas>
        </div>
        <p>Sự khác biệt rõ rệt giữa hai kỷ nguyên cho thấy ảnh hưởng to lớn của HLV Pep Guardiola và đầu tư từ chủ sở hữu Sheikh Mansour (từ 2008). Trước năm 2008, Man City là một đội bóng tầm trung với tỉ lệ thắng dưới 40%.</p>

        <table>
            <thead>
                <tr><th>Thời kỳ</th><th>Tỉ lệ thắng trung bình</th><th>Số danh hiệu lớn</th></tr>
            </thead>
            <tbody>
                <tr><td>Trước 2008 (trước thời Mansour)</td><td>~38%</td><td>2 (FA Cup 1969, ECWC 1970)</td></tr>
                <tr><td>2008-2016 (Mancini, Pellegrini)</td><td>~58%</td><td>5 (2 PL, 1 FA, 2 EFL)</td></tr>
                <tr><td>2016-2024 (Pep Guardiola)</td><td><b>~73%</b></td><td><b>18+</b> (6 PL, 2 FA, 4 EFL, 1 UCL...)</td></tr>
            </tbody>
        </table>
    </div>

    <div class="section">
        <h2>5. Yếu tố dẫn đến tỉ lệ thắng cao</h2>
        <h3>5.1. Triết lý chiến thuật của Pep Guardiola</h3>
        <p>Phong cách kiểm soát bóng (possession-based football) với trung bình <b>65-70%</b> tỉ lệ kiểm soát bóng mỗi trận giúp đội bóng chủ động và hạn chế cơ hội của đối thủ.</p>

        <h3>5.2. Chất lượng đội hình</h3>
        <p>Đầu tư mạnh vào các ngôi sao như Kevin De Bruyne, Erling Haaland, Rodri, Phil Foden - những cầu thủ hàng đầu thế giới ở vị trí của họ. Riêng Erling Haaland ghi <b>36 bàn</b> tại Premier League mùa 2022/23 - kỷ lục mọi thời đại.</p>

        <h3>5.3. Tài chính và cơ sở vật chất</h3>
        <p>Học viện City Football Academy với tổng đầu tư hơn 200 triệu bảng, hệ thống vệ tinh toàn cầu (CFG) cung cấp tài năng và dữ liệu phân tích.</p>

        <h3>5.4. Tâm lý chiến thắng</h3>
        <p>Đội bóng đã quen với áp lực vô địch, tạo nên hiệu ứng "tâm lý người chiến thắng" giúp duy trì phong độ ổn định qua các mùa giải.</p>
    </div>

    <div class="section">
        <h2>6. Kết luận</h2>
        <p>Manchester City dưới thời Pep Guardiola đã thiết lập một tiêu chuẩn mới về sự thống trị trong bóng đá Anh với tỉ lệ thắng trung bình <b>~73%</b> - một con số ấn tượng so với mức trung bình của các nhà vô địch Premier League trong lịch sử (thường khoảng 60-65%).</p>
        <p>Tuy nhiên, các thách thức trong tương lai bao gồm: (1) sự ra đi của Pep Guardiola, (2) các vụ điều tra về tài chính (115 cáo buộc của Premier League), và (3) cạnh tranh ngày càng khốc liệt từ Liverpool, Arsenal và Real Madrid trên đấu trường châu Âu.</p>

        <div class="highlight">
            <strong>Bài học cho các CLB khác:</strong> Tỉ lệ thắng cao bền vững đến từ sự kết hợp giữa <b>chiến lược dài hạn</b>, <b>đầu tư thông minh</b>, <b>HLV chất lượng</b> và <b>văn hóa chiến thắng</b> - không chỉ là tiền bạc.
        </div>

        <div class="source">
            <strong>Nguồn dữ liệu:</strong> Premier League Official Statistics, Transfermarkt, BBC Sport, Opta Sports, Manchester City FC Official Records.
            <br>Lưu ý: Một số số liệu là ước tính dựa trên dữ liệu công khai.
        </div>
    </div>

</div>

<footer>
    <p><strong>Nghiên cứu tỉ lệ thắng - Manchester City F.C.</strong></p>
    <p>Tạo ra cho mục đích học thuật và phân tích thể thao © 2026</p>
</footer>

<script>
// Biểu đồ tỉ lệ thắng theo mùa
const ctx1 = document.getElementById('seasonChart').getContext('2d');
new Chart(ctx1, {
    type: 'line',
    data: {
        labels: ['2017/18', '2018/19', '2019/20', '2020/21', '2021/22', '2022/23', '2023/24'],
        datasets: [{
            label: 'Tỉ lệ thắng (%)',
            data: [75.9, 82.0, 65.6, 68.9, 69.6, 73.8, 67.8],
            borderColor: '#1C2C5B',
            backgroundColor: 'rgba(108,171,221,0.3)',
            borderWidth: 3,
            fill: true,
            tension: 0.3,
            pointBackgroundColor: '#6CABDD',
            pointBorderColor: '#fff',
            pointRadius: 6,
            pointHoverRadius: 9
        }]
    },
    options: {
        responsive: true,
        maintainAspectRatio: false,
        plugins: {
            title: {
                display: true,
                text: 'Tỉ lệ thắng của Manchester City qua các mùa giải',
                font: { size: 16, weight: 'bold' },
                color: '#1C2C5B'
            },
            legend: { position: 'top' }
        },
        scales: {
            y: {
                beginAtZero: false,
                min: 50,
                max: 90,
                title: { display: true, text: 'Tỉ lệ thắng (%)' }
            }
        }
    }
});

// Biểu đồ so sánh kỷ nguyên
const ctx2 = document.getElementById('comparisonChart').getContext('2d');
new Chart(ctx2, {
    type: 'bar',
    data: {
        labels: ['Trước 2008', '2008-2016', '2016-2024 (Pep)'],
        datasets: [{
            label: 'Tỉ lệ thắng trung bình (%)',
            data: [38, 58, 73],
            backgroundColor: ['#94a3b8', '#6CABDD', '#1C2C5B'],
            borderRadius: 8,
            borderWidth: 0
        }]
    },
    options: {
        responsive: true,
        maintainAspectRatio: false,
        plugins: {
            title: {
                display: true,
                text: 'So sánh tỉ lệ thắng qua các kỷ nguyên',
                font: { size: 16, weight: 'bold' },
                color: '#1C2C5B'
            },
            legend: { display: false }
        },
        scales: {
            y: {
                beginAtZero: true,
                max: 100,
                title: { display: true, text: 'Tỉ lệ thắng (%)' }
            }
        }
    }
});
</script>

</body>
</html>
