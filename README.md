# my-fishing-game <!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Fishing Legend Mobile</title>
    <style>
        body { margin: 0; overflow: hidden; background: #000; touch-action: none; font-family: sans-serif; }
        canvas { display: block; background: linear-gradient(#87CEEB 20%, #1E90FF 50%, #00008B 100%); }
        #ui { 
            position: absolute; top: env(safe-area-inset-top, 20px); left: 20px; 
            color: white; font-size: 20px; font-weight: bold; text-shadow: 2px 2px #000; pointer-events: none; 
        }
    </style>
</head>
<body>
    <div id="ui">ĐIỂM: <span id="score">0</span></div>
    <canvas id="gameCanvas"></canvas>

    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');
        const scoreElement = document.getElementById('score');

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        let score = 0;
        let hookX = canvas.width / 2;
        let hookY = canvas.height * 0.5;

        // --- Cấu hình hình ảnh ---
        const playerImg = new Image();
        playerImg.src = 'https://i.imgur.com/K3ZpZ6h.png'; // Thay bằng link ảnh người cầm cần của bạn

        const fishGoldImg = new Image(); 
        fishGoldImg.src = 'https://i.imgur.com/2YyO6zX.png'; // Thay bằng link ảnh cá vàng lửa

        const fishDarkImg = new Image();
        fishDarkImg.src = 'https://i.imgur.com/vH9xH9m.png'; // Thay bằng link ảnh cá quỷ đen

        let fishes = [];

        function createFish() {
            const isLegend = Math.random() > 0.7;
            const side = Math.random() > 0.5 ? 1 : -1;
            return {
                x: side ===
                
