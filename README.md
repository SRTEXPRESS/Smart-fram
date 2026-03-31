<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<title>Soil Moisture Dashboard</title>

<!-- Chart.js -->
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<style>
body {
    font-family: Arial;
    text-align: center;
    background: #0f172a;
    color: white;
}

.circle {
    width: 180px;
    height: 180px;
    border-radius: 50%;
    margin: 30px auto;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 28px;
    background: conic-gradient(#22c55e 0%, #1e293b 0%);
    transition: 0.5s;
}

canvas {
    max-width: 600px;
    margin: auto;
}
</style>
</head>

<body>

<h1>🌱 Soil Moisture Dashboard</h1>

<div class="circle" id="circle">0%</div>

<canvas id="myChart"></canvas>

<script>
let dataPoints = [];
let labels = [];

const ctx = document.getElementById('myChart').getContext('2d');

const chart = new Chart(ctx, {
    type: 'line',
    data: {
        labels: labels,
        datasets: [{
            label: 'ความชื้นในดิน (%)',
            data: dataPoints,
            borderWidth: 2,
            tension: 0.3
        }]
    },
    options: {
        scales: {
            y: {
                min: 0,
                max: 100
            }
        }
    }
});

function updateDashboard(val){
    const circle = document.getElementById("circle");
    circle.innerText = val + "%";

    circle.style.background =
        `conic-gradient(#22c55e ${val}%, #1e293b ${val}%)`;

    // เพิ่มข้อมูลเข้า graph
    const time = new Date().toLocaleTimeString();

    labels.push(time);
    dataPoints.push(val);

    if(dataPoints.length > 10){
        dataPoints.shift();
        labels.shift();
    }

    chart.update();
}

// demo (เปลี่ยนเป็นค่าจริงได้)
setInterval(() => {
    let moisture = Math.floor(Math.random() * 100);
    updateDashboard(moisture);
}, 2000);

</script>

</body>
</html>
