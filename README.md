
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
    overflow-x:hidden;
    overflow-y:auto; /* FIXED SCROLL */
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

#ghostImage{
    position:fixed;
    top:50%;
    left:50%;
    transform:translate(-50%,-50%);
    max-width:300px;
    opacity:0;
    pointer-events:none;
    transition:opacity 0.3s;

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

<!-- RANDOM IMAGE -->
<img id="ghostImage" src="https://i.pinimg.com/originals/f1/25/20/f12520f36a9b98f6e897f0705fd0d373.gif">


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

// ----------- GLITCH SYSTEM -----------

function glitchLine(line){
    if(Math.random() < 0.08){
        return "> ███ ERROR ███ MEMORY CORRUPTED ███";
    }
    return line;
}

function corruptText(str){
    const chars = "!@#$%^&*()_+=-{}[]<>?/|";
    return str.split("").map(c=>{
        if(Math.random() < 0.05){
            return chars[Math.floor(Math.random()*chars.length)];
        }
        return c;
    }).join("");
}

function processLine(line){
    if(line.toLowerCase().includes("alice")){
        return line.replace(/alice/gi, ()=>{
            return Math.random() < 0.5
                ? "<span class='glitch'>a̸l̸i̸c̸e̸</span>"
                : "alice";
        });
    }
    return line;
}

// ----------- TYPING -----------

function type(){
    if(i < story.length){

        let line = story[i];

        line = glitchLine(line);
        line = processLine(line);
        line = corruptText(line);

        text.innerHTML += line + "\n";
        i++;

        // auto scroll
        window.scrollTo(0, document.body.scrollHeight);

        // random intrusive message
        if(Math.random() < 0.05){
            const intrude = document.createElement("div");
            intrude.classList.add("glitch");
            intrude.textContent = "> why did you erase yourself?";
            text.appendChild(intrude);
        }

        setTimeout(type, 120);

    } else {
        spawnSecret();
    }
}

// ----------- SECRET NODE -----------

function spawnSecret(){
    const secret = document.createElement("div");
    secret.classList.add("secret");
    secret.textContent = "> ...do you remember me?";

    text.appendChild(secret);

    secret.addEventListener("click", ()=>{
        window.location.href = "node4.html";
    });
}

// CURSOR FOLLOW (FIXED)
document.addEventListener("mousemove", function(e){
if(Math.random() < 0.01){
let follow = document.createElement("div")
follow.innerText = "do you remember me?"
follow.style.position="absolute"
follow.style.left = e.pageX + "px"
follow.style.top = e.pageY + "px"
follow.style.opacity="0.5"
document.body.appendChild(follow)
setTimeout(()=>follow.remove(),500)
}
})

/* ------------------ RANDOM IMAGE APPEAR ------------------ */
const ghost = document.getElementById("ghostImage");

function randomFlash(){
    const delay = Math.random() * 8000 + 4000; // 4–12 sec random

    setTimeout(()=>{
        ghost.style.opacity = "1";

        setTimeout(()=>{
            ghost.style.opacity = "0";
            randomFlash(); // loop forever
        }, 400); // visible time
    }, delay);
}

randomFlash();
/* -------------------------------------------------------- */

type();
</script>

</body>
</html>
