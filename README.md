<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Riyanshi Computer - Multi Player</title>

<style>
body{
    margin:0;
    font-family:Arial;
    background:#0f172a;
    color:white;
}

/* Header */
header{
    background:#020617;
    padding:15px;
    text-align:center;
    font-size:22px;
    font-weight:bold;
    color:#38bdf8;
}

/* Input Area */
.control{
    text-align:center;
    padding:20px;
    background:#020617;
}

input{
    width:60%;
    padding:12px;
    border-radius:6px;
    border:none;
}

button{
    padding:12px 15px;
    background:#38bdf8;
    border:none;
    color:black;
    font-weight:bold;
    border-radius:6px;
    cursor:pointer;
}

/* Grid */
.grid{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(320px,1fr));
    gap:20px;
    padding:20px;
}

/* Video Card */
.video-card{
    background:#020617;
    border-radius:10px;
    padding:10px;
    box-shadow:0 0 15px rgba(0,0,0,0.7);
    position:relative;
    border:2px solid #1e293b;
}

/* FREE TAG */
.free-tag{
    font-size:12px;
    margin-bottom:5px;
    display:flex;
    align-items:center;
    gap:6px;
    color:#22c55e;
    font-weight:bold;
}

.free-dot{
    width:8px;
    height:8px;
    background:#22c55e;
    border-radius:50%;
}

/* Computer dots */
.card-header{
    display:flex;
    gap:5px;
    margin-bottom:8px;
}

.dot{
    width:10px;
    height:10px;
    border-radius:50%;
}

.red{background:#ef4444;}
.yellow{background:#facc15;}
.green{background:#22c55e;}

iframe{
    width:100%;
    height:200px;
    border-radius:6px;
}

/* Remove */
.remove{
    position:absolute;
    top:8px;
    right:8px;
    background:red;
    color:white;
    border:none;
    padding:5px 8px;
    cursor:pointer;
    border-radius:5px;
}
/* ===== FOOTER ===== */
footer{
  position:fixed;
  bottom:0;
  left:0;
  width:100%;
  background:#34495e;
  color:white;
  text-align:center;
  padding:10px;
}
footer a{
  color:white;
  margin:0 5px;
  text-decoration:underline;
}
</style>

</head>

<body>

<header>🖥️ RIYANSHI COMPUTER🖥️ - MULTI PLAYER</header>

<div class="control">
    <input type="text" id="link" placeholder="Paste YouTube Link">
    <button onclick="addVideo()">Add Video</button>
</div>

<div class="grid" id="players"></div>

<script src="https://www.youtube.com/iframe_api"></script>

<script>
function extractID(url){
    try{
        let u = new URL(url);
        if(u.hostname === "youtu.be"){
            return u.pathname.substring(1);
        }
        return u.searchParams.get("v");
    }catch{
        return null;
    }
}

function addVideo(){
    let url = document.getElementById("link").value;
    let id = extractID(url);

    if(!id){
        alert("Valid YouTube link daalo");
        return;
    }

    let card = document.createElement("div");
    card.className = "video-card";

    // FREE TAG
    let freeTag = document.createElement("div");
    freeTag.className = "free-tag";
    freeTag.innerHTML = `
        <div class="free-dot"></div>
        🖥️RIYANSHI COMPUTER🖥️`;

    // Computer header
    let header = document.createElement("div");
    header.className = "card-header";
    header.innerHTML = `
        <div class="dot red"></div>
        <div class="dot yellow"></div>
        <div class="dot green"></div>
    `;

    // Remove button
    let removeBtn = document.createElement("button");
    removeBtn.innerText = "X";
    removeBtn.className = "remove";
    removeBtn.onclick = () => card.remove();

    let playerDiv = document.createElement("div");

    card.appendChild(freeTag);
    card.appendChild(header);
    card.appendChild(removeBtn);
    card.appendChild(playerDiv);

    document.getElementById("players").appendChild(card);

    new YT.Player(playerDiv, {
        height: "200",
        width: "100%",
        videoId: id,
        playerVars: {
            autoplay: 1,
            mute: 1
        }
    });

    document.getElementById("link").value = "";
}
</script>
<footer>
  <p>© 2025 <b>Riyanshi Computer</b> | बलुआ, सीतामढ़ी, बिहार</p>
  <p>📞 7277110546 | 📍 843327</p>
  <div>
    <a href="#">Help</a> |
    <a href="#">Feedback</a> |
    <a href="#">Privacy</a>
  </div>
</footer>

</body>
</html>