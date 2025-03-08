<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>生日快乐</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background: black;
            color: white;
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        canvas {
            position: absolute;
            top: 0;
            left: 0;
        }
        .text {
            font-size: 50px;
            position: relative;
            z-index: 1;
        }
        .name {
            font-size: 70px;
            position: absolute;
            z-index: 2;
            color: pink;
            animation: blink 1s infinite;
        }
        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0; }
        }
    </style>
</head>
<body>
    <div class="text" id="loveText">LOVE</div>
    <div class="text" id="birthdayText" style="display: none;">生日快乐</div>
    <div class="name" id="nameText" style="display: none;">张淼淼</div>
    <canvas id="fireworksCanvas"></canvas>

    <script>
        const canvas = document.getElementById('fireworksCanvas');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const loveText = document.getElementById('loveText');
        const birthdayText = document.getElementById('birthdayText');
        const nameText = document.getElementById('nameText');

        let loveX = Math.random() * canvas.width;
        let loveY = -50;
        let loveSpeed = 3;
        let fireworks = [];
        let showBirthday = false;
        let showName = false;
        let fireworkCount = 0;
        let lastFireworkTime = 0;
        const startTime = Date.now();

        const COLORS = [
            'rgb(255, 0, 0)',    // 红色
            'rgb(0, 255, 0)',    // 绿色
            'rgb(0, 0, 255)',    // 蓝色
            'rgb(255, 255, 0)',  // 黄色
            'rgb(255, 0, 255)', // 紫色
            'rgb(0, 255, 255)', // 青色
            'rgb(255, 165, 0)'  // 橙色
        ];

    //流动"爱"文字
    函数moveLoveText(){
    lovey+=loveSpeed；
    if(lovey>canvas.height){
    lovey=-50；
    Lovex=Math.random()*canvas.width；
    }
    loveText.style.left=Lovex+'px'；
    loveText.style.top=lovey+'px'；
    }

    // 烟花粒子类
    类粒子{
    构造函数(x，y，color){
    this.x=x；
    this.y=y；
    this.vx=Math.random()*4-2；
    this.vy=Math.random()*-5-1；
    this.color=color；
    this.lifetime=60；
    }
    update(){
    this.x+=this.vx；
    this.y+=this.vy；
    this.vy+=0.1；//重力效果
    今生今世--；
    }
    draw(){
    if(this.lifetime>0){
    ctx.fillStyle=this.color；
    ctx.beginPath()；
    ctx.arc(this.x，this.y，5，0，Math.PI*2)；
    ctx.fill()；
    }
    }
    }

    // 创建烟花
    函数createFirework(x，y，color，numParticles=100){
    for(让i=0；i<numParticle；i++){
    fireworks.push(新建粒子(x，y，颜色))；
    }
    }

    // 主循环
    函数animate(){
    ctx.clearRect(0，0，canvas.width，canvas.height)；

    moveLoveText()；

    Const currentTime=Date.now()；
    Const eapsedTime=(currentTime-startTime)/1000；

    // 最后3秒显示烟花和“生日快乐”
    if(eapsedTime>=7){
    if(！showBirthday){
    showBirthday=true；
    birthyText.style.display='block'；
    createFirework(canvas.width/2，canvas.height/2，COLORS[FireworkCount%colors.length])；
    fireworkCount++；
    lastFireworkTime=当前时间；
    }

    // 每隔0.5秒生成一个新的烟花
    if(currentTime-lastFireworkTime>500&&fireworkCount<7){
    createFirework(canvas.width/2，canvas.height/2，COLORS[FireworkCount%colors.length])；
    fireworkCount++；
    lastFireworkTime=当前时间；
    }

    // 最后一个烟花效果更好看
    if(fireworkCount===7){
    createFirework(canvas.width/2，canvas.height/2，COLORS[6]，200)；
    }

    // 更新和绘制烟花
    fireworks.forEach((粒子，索引)=>{
    particle.update()；
    particle.draw()；
    if(particle.lifetime<=0){
    #生日_
