<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<title>Soil Moisture Dashboard</title>
<style>
    body {
        font-family: Arial;
        text-align: center;
        background: #0f172a;
        color: white;
    }

    h1 {
        margin-top: 30px;
    }

    .circle {
        width: 200px;
        height: 200px;
        border-radius: 50%;
        margin: 50px auto;
        position: relative;
        background: conic-gradient(#22c55e 0%, #1e293b 0%);
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 32px;
        transition: 0.5s;
    }

    .status {
        font-size: 20px;
        margin-top: 10px;
    }

    .low { color: red; }
    .medium { color: orange; }
    .high { color: lightgreen; }

    /* animation น้ำ */
    .wave {
        position: absolute;
        width: 200%;
        height: 200%;
        background: rgba(34,197,94,0.3);
        top: 50%;
        left: -50%;
        border-radius: 40%;
        animation: wave 4s infinite linear;
    }

    @keyframes wave {
        0% { transform: rotate(0deg); }
        100% { transform: rotate(360deg); }
    }
</style>
</head>

<body>

<h1>🌱 Soil Moisture Dashboard</h1>

<div class="circle" id="circle">
    <div class="wave"></div>
    <span id="value">0%</span>
</div>

<div class="status" id="status">Loading...</div>

<script>
let moisture = 30; // 👈 เปลี่ยนค่านี้ (หรือรับจาก Pico)

function updateDashboard(val){
    const circle = document.getElementById("circle");
    const text = document.getElementById("value");
    const status = document.getElementById("status");

    text.innerText = val + "%";

    // วงกลม
    circle.style.background =
        `conic-gradient(#22c55e ${val}%, #1e293b ${val}%)`;

    // สถานะ
    if(val < 30){
        status.innerText = "ดินแห้ง 🌵";
        status.className = "status low";
    } else if(val < 70){
        status.innerText = "กำลังดี 🌿";
        status.className = "status medium";
    } else {
        status.innerText = "ชื้นมาก 💧";
        status.className = "status high";
    }
}

// demo animation
setInterval(() => {
    moisture = Math.floor(Math.random() * 100);
    updateDashboard(moisture);
}, 2000);

</script>

</body>
</html>
