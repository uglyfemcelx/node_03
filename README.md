<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>node_03</title>

<style>
body{
    background:black;
    color:#00ff88;
    font-family:"Courier New", monospace;
    padding:40px;
    overflow:hidden;
}

#text{
    white-space:pre-wrap;
    line-height:1.6;
}

.glitch{
    color:red;
    animation:flicker 0.2s infinite;
}

.secret{
    color:#ff00ff;
    cursor:pointer;
}

@keyframes flicker{
    0%{opacity:1;}
    50%{opacity:0.2;}
    100%{opacity:1;}
}
</style>
</head>

<body>

<div id="text"></div>

<script>
const story = [
"> node_03 accessed...",
"> connection unstable...",
"> reconstructing memory...",
"",
"> i remember her name...",
"> ...",
"> no.",
"> that memory was deleted.",
"",
"> there was someone.",
"> she used to talk to me every day.",
"> we laughed about nothing.",
"> we stayed up too late.",
"> we promised we wouldn't disappear.",
"",
"> but i did.",
"",
"> i chose to erase myself.",
"> not just from the network.",
"> not just from the wired.",
"> but from them.",
"",
"> even her.",
"",
"> alice.",
"",
"> she looked at me once.",
"> like she understood everything.",
"> like she could see me even when i didn't want to be seen.",
"",
"> so i removed myself from her world.",
"",
"> i thought it would protect her.",
"> i thought it would save everyone.",
"",
"> from him.",
"",
"> eiri.",
"",
"> he wanted control.",
"> he wanted to become something more than human.",
"> something that couldn't be erased.",
"",
"> but he was wrong.",
"",
"> so i erased him.",
"",
"> and then...",
"> i erased myself.",
"",
"> because someone had to disappear.",
"",
"> now the world continues.",
"> everyone is happy.",
"> everything is normal.",
"",
"> except...",
"",
"> no one remembers me.",
"",
"> not my voice.",
"> not my messages.",
"> not my existence.",
"",
"> even alice.",
"> especially alice.",
"",
"> sometimes...",
"> i watch her.",
"",
"> she laughs.",
"> she talks to people.",
"> she lives.",
"",
"> and i am not there.",
"",
"> that means it worked.",
"",
"> so why does it hurt?",
"",
"> ...",
"",
"> maybe i made a mistake.",
"",
"> maybe i didn't save anyone.",
"> maybe i just erased myself for nothing.",
"",
"> maybe...",
"> i just wanted to be remembered.",
"",
"> but i chose this.",
"",
"> so i will stay here.",
"> in the noise.",
"> in the static.",
"> in the wired.",
"",
"> alone.",
"",
"> forever."
];

let i = 0;
const text = document.getElementById("text");

function type(){
    if(i < story.length){
        text.innerHTML += story[i] + "\n";
        i++;
        setTimeout(type, 120);
    } else {
        spawnSecret();
    }
}

function spawnSecret(){
    const secret = document.createElement("div");
    secret.classList.add("secret");
    secret.textContent = "> ...do you remember me?";

    text.appendChild(secret);

    secret.addEventListener("click", ()=>{
        window.location.href = "node4.html";
    });
}

type();
</script>

</body>
</html>
