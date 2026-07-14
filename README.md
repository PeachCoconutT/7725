<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>松柏花园物业系统</title>

<style>

body{
    background:#111;
    color:#00ff88;
    font-family:Consolas,monospace;
    margin:0;
    padding:0;
}

header{
    background:#000;
    padding:20px;
    border-bottom:1px solid #00ff88;
}

h1{
    margin:0;
}

.container{
    padding:20px;
}

.card{
    border:1px solid #00ff88;
    margin-bottom:20px;
    padding:15px;
}

button{
    background:black;
    color:#00ff88;
    border:1px solid #00ff88;
    padding:8px 15px;
    cursor:pointer;
}

button:hover{
    background:#00ff88;
    color:black;
}

.hidden{
    display:none;
}

input{
    background:black;
    color:#00ff88;
    border:1px solid #00ff88;
    padding:8px;
}

#terminal{
    background:black;
    padding:10px;
    height:200px;
    overflow:auto;
    border:1px solid #00ff88;
}

.glitch{
    animation:glitch 0.2s infinite;
}

@keyframes glitch{
    0%{transform:translate(1px,1px);}
    50%{transform:translate(-1px,-1px);}
    100%{transform:translate(1px,-1px);}
}

</style>
</head>

<body>

<header>
<h1>松柏花园物业管理系统 V1.3</h1>
<p>内部资料 请勿传播</p>
</header>

<div class="container">

<div class="card">
<h2>住户查询</h2>

<button onclick="showResident('101')">101室</button>
<button onclick="showResident('203')">203室</button>
<button onclick="showResident('305')">305室</button>
<button onclick="showResident('404')">404室</button>

<div id="residentInfo" style="margin-top:20px;"></div>

</div>

<div class="card">
<h2>物业日志</h2>

<div id="terminal">

[2025-03-14] 电力检修完成<br>
[2025-03-15] 13栋监控异常<br>
[2025-03-15] 404档案锁定<br>
[ERROR] ACCESS DENIED
</div>

</div>

<div class="card">

<h2>管理员入口</h2>

<input id="password" placeholder="输入密码">
<button onclick="login()">登录</button>

<div id="adminPanel" class="hidden">

<h3>机密档案</h3>

<p>
项目名称：启明计划
</p>

<p>
实验区域：松柏花园
</p>

<p>
状态：运行中
</p>

<p>
Subject-0013 状态：观察中
</p>

</div>

</div>

<div id="ending" class="card hidden">

<h2>实验完成</h2>

<p id="playerData"></p>

</div>

</div>

<script>

let clickCount = 0;
let startTime = Date.now();

document.addEventListener("click",()=>{
    clickCount++;
});

function showResident(room){

let box=document.getElementById("residentInfo");

if(room==="101"){
box.innerHTML=`
<h3>101室</h3>
<p>独居老人</p>
<p>记录：每天17:30准时关灯</p>
`;
}

if(room==="203"){
box.innerHTML=`
<h3>203室</h3>
<p>钢琴教师</p>
<p>备注：邻居称其已搬离五年</p>
`;
}

if(room==="305"){
box.innerHTML=`
<h3>305室</h3>
<p>门口常出现儿童鞋</p>
<p>实际无儿童居住</p>
`;
}

if(room==="404"){
box.innerHTML=`
<h3>404室</h3>
<p style="color:red;">
档案不存在
</p>

<p>
提示：
物业日志中的日期可能有问题
</p>
`;
}

}

function login(){

let pwd=document.getElementById("password").value;

if(pwd==="314"){

document.getElementById("adminPanel")
.classList.remove("hidden");

setTimeout(showEnding,5000);

}else{

alert("密码错误");

}

}

function showEnding(){

let time=Math.floor(
(Date.now()-startTime)/1000
);

document.body.classList.add("glitch");

document.getElementById("ending")
.classList.remove("hidden");

document.getElementById("playerData")
.innerHTML=`

你已被观察。<br><br>

停留时间：
${time}秒<br>

点击次数：
${clickCount}<br><br>

被试者编号：Subject-0013

`;

}

</script>

</body>
</html>
