<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Smart Farm Dashboard</title>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<style>
body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #0f172a;
    color: white;
    text-align: center;
}

h1 {
    margin-top: 20px;
    color: #38bdf8;
}

.circle {
    width: 200px;
    height: 200px;
    border-radius: 50%;
    margin: 30px auto;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 32px;
    background: conic-gradient(#22c55e 0%, #1e293b 0%);
}

canvas {
    max-width: 600px;
    margin: auto;
}
</style>
</head>

<body>

<h1>Smart Farm</h1>
<h2>🌱 Soil Moisture Dashboard</h2>

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
            label: 'ความชื้น (%)',
            data: dataPoints,
            borderWidth: 2
        }]
    },
    options: {
        scales: {
            y: { min: 0, max: 100 }
        }
    }
});

function updateDashboard(val){
    document.getElementById("circle").innerText = val + "%";

    labels.push(new Date().toLocaleTimeString());
    dataPoints.push(val);

    if(dataPoints.length > 10){
        labels.shift();
        dataPoints.shift();
    }

    chart.update();
}

setInterval(() => {
    let moisture = Math.floor(Math.random() * 100);
    updateDashboard(moisture);
}, 2000);

</script>

</body>
</html>
