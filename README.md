<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Exam Portal</title>
<style>
body{
font-family:Arial;
background:#f2f2f2;
padding:20px;
}
.container{
max-width:800px;
margin:auto;
background:white;
padding:20px;
border-radius:10px;
}
h1{
text-align:center;
}
.question{
margin-top:20px;
}
button{
padding:10px 20px;
font-size:18px;
margin-top:20px;
}
.correct{
color:green;
}
.wrong{
color:red;
}
#timer{
font-size:22px;
color:red;
text-align:right;
}
</style>
</head>

<body>

<div class="container">

<h1>SSC Mock Test</h1>

<div id="timer">05:00</div>

<form id="quiz">

<div class="question">
<b>1. 24 ÷ 6 × 3 + 2 = ?</b><br>
<input type="radio" name="q1" value="10">10<br>
<input type="radio" name="q1" value="12">12<br>
<input type="radio" name="q1" value="14">14<br>
<input type="radio" name="q1" value="18">18<br>
</div>

<div class="question">
<b>2. 20% of 250 = ?</b><br>
<input type="radio" name="q2" value="40">40<br>
<input type="radio" name="q2" value="45">45<br>
<input type="radio" name="q2" value="50">50<br>
<input type="radio" name="q2" value="55">55<br>
</div>

<div class="question">
<b>3. Ravi walks North then East. Final direction?</b><br>
<input type="radio" name="q3" value="North">North<br>
<input type="radio" name="q3" value="South">South<br>
<input type="radio" name="q3" value="North-East">North-East<br>
<input type="radio" name="q3" value="West">West<br>
</div>

<div class="question">
<b>4. A sits second from left. C sits right of A. Who is right of A?</b><br>
<input type="radio" name="q4" value="B">B<br>
<input type="radio" name="q4" value="C">C<br>
<input type="radio" name="q4" value="D">D<br>
<input type="radio" name="q4" value="E">E<br>
</div>

<div class="question">
<b>5. 15% of 600 = ?</b><br>
<input type="radio" name="q5" value="80">80<br>
<input type="radio" name="q5" value="85">85<br>
<input type="radio" name="q5" value="90">90<br>
<input type="radio" name="q5" value="95">95<br>
</div>

<button type="button" onclick="submitTest()">Submit Test</button>

</form>

<div id="result"></div>

</div>

<script>

let time=300;

let x=setInterval(function(){

let m=Math.floor(time/60);

let s=time%60;

document.getElementById("timer").innerHTML=
(m<10?"0"+m:m)+":"+(s<10?"0"+s:s);

time--;

if(time<0){

clearInterval(x);

submitTest();

}

},1000);

function submitTest(){

clearInterval(x);

let score=0;

let ans={
q1:"14",
q2:"50",
q3:"North-East",
q4:"C",
q5:"90"
};

let exp={
q1:"24÷6=4, 4×3=12, 12+2=14",
q2:"20/100 ×250 =50",
q3:"North then East = North-East",
q4:"C sits immediately right of A.",
q5:"15% of 600 =90"
};

let html="<h2>Result</h2>";

for(let i=1;i<=5;i++){

let q="q"+i;

let user=document.querySelector('input[name="'+q+'"]:checked');

if(user && user.value==ans[q]){

score++;

html+="<p class='correct'>Q"+i+" Correct ✅<br>"+exp[q]+"</p>";

}

else{

html+="<p class='wrong'>Q"+i+" Wrong ❌<br>Correct Answer : "+ans[q]+"<br>"+exp[q]+"</p>";

}

}

html+="<h2>Score : "+score+"/5</h2>";

document.getElementById("result").innerHTML=html;

}

</script>

</body>
</html>
