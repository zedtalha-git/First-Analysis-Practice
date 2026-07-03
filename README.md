# First-Analysis-Practice
Created GitHub account for first practice 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Calculator</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial, Helvetica, sans-serif;
}

body{
    background:linear-gradient(135deg,#4facfe,#00f2fe);
    display:flex;
    justify-content:center;
    align-items:center;
    height:100vh;
}

.calculator{
    background:#1e1e2f;
    padding:20px;
    border-radius:15px;
    box-shadow:0 10px 25px rgba(0,0,0,0.3);
}

#display{
    width:100%;
    height:60px;
    margin-bottom:15px;
    border:none;
    outline:none;
    border-radius:10px;
    background:#2d2d44;
    color:white;
    text-align:right;
    font-size:2rem;
    padding:10px;
}

.buttons{
    display:grid;
    grid-template-columns:repeat(4,70px);
    gap:10px;
}

button{
    height:60px;
    border:none;
    border-radius:10px;
    font-size:1.2rem;
    cursor:pointer;
    background:#3c3c5c;
    color:white;
    transition:0.2s;
}

button:hover{
    background:#57577d;
}

.operator{
    background:#ff9500;
}

.operator:hover{
    background:#ffad33;
}

.equal{
    background:#28a745;
}

.equal:hover{
    background:#34c759;
}

.clear{
    background:#dc3545;
}

.clear:hover{
    background:#ff4d5a;
}
</style>
</head>

<body>

<div class="calculator">
    <input type="text" id="display" readonly>

    <div class="buttons">
        <button class="clear" onclick="clearDisplay()">C</button>
        <button onclick="deleteLast()">⌫</button>
        <button class="operator" onclick="append('%')">%</button>
        <button class="operator" onclick="append('/')">÷</button>

        <button onclick="append('7')">7</button>
        <button onclick="append('8')">8</button>
        <button onclick="append('9')">9</button>
        <button class="operator" onclick="append('*')">×</button>

        <button onclick="append('4')">4</button>
        <button onclick="append('5')">5</button>
        <button onclick="append('6')">6</button>
        <button class="operator" onclick="append('-')">−</button>

        <button onclick="append('1')">1</button>
        <button onclick="append('2')">2</button>
        <button onclick="append('3')">3</button>
        <button class="operator" onclick="append('+')">+</button>

        <button onclick="append('0')">0</button>
        <button onclick="append('.')">.</button>
        <button class="equal" onclick="calculate()">=</button>
    </div>
</div>

<script>
const display = document.getElementById("display");

function append(value){
    display.value += value;
}

function clearDisplay(){
    display.value = "";
}

function deleteLast(){
    display.value = display.value.slice(0,-1);
}

function calculate(){
    try{
        display.value = eval(display.value);
    }catch{
        display.value = "Error";
    }
}

// Keyboard support
document.addEventListener("keydown", (e)=>{
    if("0123456789+-*/.%".includes(e.key)){
        append(e.key);
    }else if(e.key==="Enter"){
        e.preventDefault();
        calculate();
    }else if(e.key==="Backspace"){
        deleteLast();
    }else if(e.key==="Escape"){
        clearDisplay();
    }
});
</script>

</body>
</html>
