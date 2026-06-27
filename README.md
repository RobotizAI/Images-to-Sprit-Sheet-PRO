<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Image to Sprit Sheet PRO - RobotizAI</title>

<style>
*{
    box-sizing:border-box;
}

body{
    font-family:sans-serif;
    background:linear-gradient(135deg,#1e1e2f,#2e2e2e);
    color:#eee;
    padding:30px;
}

.container{
    max-width:900px;
    margin:auto;
    background:#1b1b2b;
    padding:30px;
    border-radius:14px;
    box-shadow:20 15px 40px rgba(0,0,0,0.6);
}

.logo{
    display:block;
    margin:0 auto 15px auto;
    max-width:220px;
}

h2{
    text-align:center;
    margin-bottom:5px;
}

.subtitle{
    text-align:center;
    opacity:0.8;
    margin-bottom:25px;
    font-size:14px;
}

.grid{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:20px;
    margin-top:20px;
}

.input-group{
    display:flex;
    flex-direction:column;
    gap:6px;
    padding:12px;
    background:#23233a;
    border-radius:10px;
    width:100%;
}

input{
    width:100%;
    padding:12px;
    border-radius:8px;
    border:none;
    background:#2e2e3e;
    color:#fff;
}

label{
    font-size:13px;
    opacity:0.8;
}

button{
    padding:14px 18px;
    border-radius:12px;
    cursor:pointer;
    background:linear-gradient(180deg,#4f8fc9 0%,#2f6fa3 50%,#1f4f7a 100%);
    color:#fff;
    font-weight:bold;
    border:2px solid #ffffff;
    box-shadow:10px 10px 15px rgba(0,0,0,0.5);
    transition:all 0.15s ease;
    letter-spacing:0.5px;
}

button:hover{
    transform:translateY(-2px);
    background:linear-gradient(180deg,#5fa3e0 0%,#3a7fb8 50%,#276295 100%);
    box-shadow:12px 12px 18px rgba(0,0,0,0.6);
}

button:active{
    transform:translateY(2px);
    background:linear-gradient(180deg,#3f7fb8 0%,#2a6394 50%,#1a476f 100%);
    box-shadow:6px 6px 10px rgba(0,0,0,0.5);
}




.actions{
    display:flex;
    gap:15px;
    margin-top:25px;
}

canvas{
    margin-top:25px;
    width:100%;
    background:#111;
    border-radius:10px;
}
</style>
</head>
<body>

<div class="container">

<img class="logo" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAfAAAAEICAMAAACXs1agAAAACXBIWXMAAAsTAAALEwEAmpwYAAANeGlUWHRYTUw6Y29tLmFkb2JlLnhtcAAAAAAAPD94cGFja2V0IGJlZ2luPSLvu78iIGlkPSJXNU0wTXBDZWhpSHpyZVN6TlRjemtjOWQiPz4KPHg6eG1wbWV0YSB4bWxuczp4PSJhZG9iZTpuczptZXRhLyIgeDp4bXB0az0iWE1QIENvcmUgNC40LjAtRXhpdjIiPgogPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4KICA8cmRmOkRlc2NyaXB0aW9uIHJkZjphYm91dD0iIgogICAgeG1sbnM6eG1wTU09Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9tbS8iCiAgICB4bWxuczpzdEV2dD0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL3NUeXBlL1Jlc291cmNlRXZlbnQjIgogICAgeG1sbnM6ZGM9Imh0dHA6Ly9wdXJsLm9yZy9kYy9lbGVtZW50cy8xLjEvIgogICAgeG1sbnM6R0lNUD0iaHR0cDovL3d3dy5naW1wLm9yZy94bXAvIgogICAgeG1sbnM6dGlmZj0iaHR0cDovL25zLmFkb2JlLmNvbS90aWZmLzEuMC8iCiAgICB4bWxuczp4bXA9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC8iCiAgIHhtcE1NOkRvY3VtZW50SUQ9ImdpbXA6ZG9jaWQ6Z2ltcDpmNmY3MmEzNC00ZTg4LTQyZTAtYTYyMC1hNzE5MWRlZTQ4MGUiCiAgIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6ZDY0OTQ2NWMtNTYwNS00ZjBiLWI1Y2YtN2Y1Y2YyYjlmYTQ0IgogICB4bXBNTTpPcmlnaW5hbERvY3VtZW50SUQ9InhtcC5kaWQ6OTRhZjAxZjItOGY4NS00OWJjLTkxMjItMDM4N2FmYjE4MDA4IgogICBkYzpGb3JtYXQ9ImltYWdlL3BuZyIKICAgR0lNUDpBUEk9IjIuMCIKICAgR0lNUDpQbGF0Zm9ybT0iTGludXgiCiAgIEdJTVA6VGltZVN0YW1wPSIxNzQ5NzkzMzk4MjI3OTU4IgogICBHSU1QOlZlcnNpb249IjIuMTAuMzYiCiAgIHRpZmY6T3JpZW50YXRpb249IjEiCiAgIHhtcDpDcmVhdG9yVG9vbD0iR0lNUCAyLjEwIgogICB4bXA6TWV0YWRhdGFEYXRlPSIyMDI1OjA2OjEzVDAyOjQzOjE1LTAzOjAwIgogICB4bXA6TW9kaWZ5RGF0ZT0iMjAyNTowNjoxM1QwMjo0MzoxNS0wMzowMCI+CiAgIDx4bXBNTTpIaXN0b3J5PgogICAgPHJkZjpTZXE+CiAgICAgPHJkZjpsaQogICAgICBzdEV2dDphY3Rpb249InNhdmVkIgogICAgICBzdEV2dDpjaGFuZ2VkPSIvIgogICAgICBzdEV2dDppbnN0YW5jZUlEPSJ4bXAuaWlkOmVkMmE4MWExLWE2ODUtNDU4Yy04ZDFlLWIzYjFlMzFlODAzOCIKICAgICAgc3RFdnQ6c29mdHdhcmVBZ2VudD0iR2ltcCAyLjEwIChMaW51eCkiCiAgICAgIHN0RXZ0OndoZW49IjIwMjUtMDYtMTNUMDI6NDM6MTgtMDM6MDAiLz4KICAgIDwvcmRmOlNlcT4KICAgPC94bXBNTTpIaXN0b3J5PgogIDwvcmRmOkRlc2NyaXB0aW9uPgogPC9yZGY6UkRGPgo8L3g6eG1wbWV0YT4KICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgCiAgICAgICAgICAgICAgICAgICAgICAgICAgIAo8P3hwYWNrZXQgZW5kPSJ3Ij8+7eDyEAAAAMR6VFh0UmF3IHByb2ZpbGUgdHlwZSBleGlmAAB42m1Q2w3DIAz8Z4qO4BeOGYc0idQNOn4NBim0PQnfxYaL7XS+X1d6NBBKkryZFlVwSJFC1YVBoPaIID12XFPhmk/+KCQ5szNHwTQYZ348mIzVVb4Z2XMU9rVQJJjsy4iCuHXU9DGMyjBiigIOgxpjgRbb7iPsJ6ywOG00EFvb/vnefHtH9v8w0cnI4JFZowFuJyeuLtQjsjfVk5XFr7XMHNUX8m9PE+kDMs1ZSIirp5kAAAMAUExURUdwTP///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////2Xj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">

<h2>Images to Sprit Sheet PRO v71 - RobotzAI.com</h2>
<p class="subtitle">Orgulhosamente desenvolvido por Carlos Stringuetti - RobotizAI.com</p>
<p class="text" style="text-align:center; font-size:12px;"><a href="https://robotizai.com" target="_blank" style="color:#fff; text-decoration:underline;">Clique aqui para saber mais sobre a RobotizAI.com</a></p>
<p class="text" style="text-align:center; font-size:12px; color:#fff;">Crie uma conta gratuita e comece agora mesmo!</p>
<br>
<div class="text" style="font-size:13px; color:#fff; margin:0 auto 20px auto; max-width:760px;">
    <details style="background:#23233a; border-radius:10px; padding:12px 16px; margin-bottom:10px;">
        <summary style="cursor:pointer; font-size:20px; font-weight:bold; text-align:center;">Para que serve o Images to Sprit Sheet PRO?</summary>
        <p style="font-size:13px; line-height:1.6; text-align:left; margin-top:12px;">
            O Images to Sprit Sheet PRO serve para transformar uma sequência de imagens em uma única sprite sheet. Ele organiza os arquivos selecionados em linhas e colunas dentro de um canvas, permitindo gerar uma imagem PNG final e um arquivo JSON com as posições dos frames. É útil para animações, jogos, vídeos, personagens, efeitos visuais, assets para engines e qualquer projeto que precise reunir vários frames em uma imagem única.
        </p>
    </details>

    <details style="background:#23233a; border-radius:10px; padding:12px 16px; margin-bottom:10px;">
        <summary style="cursor:pointer; font-size:20px; font-weight:bold; text-align:center;">Como usar o Images to Sprit Sheet PRO?</summary>
        <p style="font-size:13px; line-height:1.6; text-align:left; margin-top:12px;">
            Clique em “Escolher arquivos” e selecione as imagens que serão usadas como frames. Ajuste a quantidade de linhas e colunas, defina o número máximo de imagens, o espaçamento, a largura e a altura da sprite sheet final. Se quiser pular frames, altere o campo “Intervalo de Frames”. Depois clique em “Gerar Sprit Sheet” para visualizar o resultado. Ao finalizar, use “Download PNG” para baixar a imagem final e “Download JSON” para baixar o mapeamento dos frames.
        </p>
    </details>
</div>
<br>

<input type="file" id="files" multiple style="margin-bottom:20px; width:100%;">

<div id="info" style="margin-bottom:15px; font-size:14px; opacity:0.85;"></div>

<div class="grid">
    <div class="input-group">
        <label>Linhas</label>
        <input id="rows" value="6" oninput="updateMaxImages()">
    </div>
    <div class="input-group">
        <label>Colunas</label>
        <input id="cols" value="6" oninput="updateMaxImages()">
    </div>

    <div class="input-group">
        <label>Máx imagens</label>
        <input id="max" value="36">
    </div>
    <div class="input-group">
        <label>Espaçamento</label>
        <input id="pad" value="0">
    </div>

    <div class="input-group">
        <label>Largura</label>
        <input id="outW" value="1024">
    </div>
    <div class="input-group">
        <label>Altura</label>
        <input id="outH" value="1024">
    </div>

    <div class="input-group">
        <label>Intervalo de Frames</label>
        <input id="step" value="1">
    </div>
</div>

<div class="actions">
    <button onclick="generate()">Gerar Sprit Sheet</button>
    <button onclick="resetPage()">Criar Novo Sprit Sheet</button>
</div><br><br><br>

<div>
    <button onclick="download()">Download PNG</button>
    <button onclick="exportJSON()">Download JSON</button>
</div>

<canvas id="canvas"></canvas>

</div>

<script>
let images=[]

const inputMax=document.getElementById('max');
inputMax.addEventListener('input',()=>{inputMax.dataset.manual='true';});

function updateMaxImages(){
 let rows = +document.getElementById("rows").value || 0
 let cols = +document.getElementById("cols").value || 0
 let max = rows * cols

 document.getElementById("max").value = max
}

document.getElementById("files").onchange = e=>{
 loadFiles(e.target.files)
}

async function loadFiles(files){
 images = await Promise.all(
  Array.from(files).map(f => createImageBitmap(f))
 )

 let total = images.length
 let max = +document.getElementById("max").value

 let step = Math.max(1, Math.floor(total / max))

 document.getElementById("info").innerText =
  "Total de imagens: " + total +
  " | Intervalo ideal sugerido: " + step

 document.getElementById("step").value = step
}

function generate(){
 if(images.length==0) return alert("Nenhuma imagem")

 let rows = +document.getElementById("rows").value
 let cols = +document.getElementById("cols").value
 let pad = +document.getElementById("pad").value
 let max = +document.getElementById("max").value
 let outW = +document.getElementById("outW").value
 let outH = +document.getElementById("outH").value
 let step = Math.max(1, +document.getElementById("step").value)

 let imgs = []

 for(let i=0; i<parseInt(document.getElementById('max').value)||0; i++){
  let idx = i * step
  if(idx >= images.length) idx = images.length - 1
  imgs.push(images[idx])
 }

 let canvas = document.getElementById("canvas")
 let ctx = canvas.getContext("2d")

 ctx.imageSmoothingEnabled = false

 canvas.width = outW
 canvas.height = outH

 let cellW = Math.floor((outW - (cols-1)*pad)/cols)
 let cellH = Math.floor((outH - (rows-1)*pad)/rows)

 ctx.clearRect(0,0,canvas.width,canvas.height)

 imgs.forEach((img,i)=>{
  let x = Math.floor((i%cols)*(cellW+pad))
  let y = Math.floor(Math.floor(i/cols)*(cellH+pad))

  let scale = Math.max(cellW / img.width, cellH / img.height)
  let dw = img.width * scale
  let dh = img.height * scale

  let dx = x + (cellW - dw) / 2
  let dy = y + (cellH - dh) / 2

  ctx.drawImage(img, dx, dy, dw, dh)
 })
}

function resetPage(){
 location.reload()
}

function download(){
 let link=document.createElement("a")
 link.download="spritesheet.png"
 link.href=document.getElementById("canvas").toDataURL()
 link.click()
}

function exportJSON(){
 let rows = +document.getElementById("rows").value
 let cols = +document.getElementById("cols").value
 let pad = +document.getElementById("pad").value
 let max = +document.getElementById("max").value
 let outW = +document.getElementById("outW").value
 let outH = +document.getElementById("outH").value
 let step = Math.max(1, +document.getElementById("step").value)

 let cellW = Math.floor((outW - (cols-1)*pad)/cols)
 let cellH = Math.floor((outH - (rows-1)*pad)/rows)

 let data={frames:{}}

 for(let i=0; i<parseInt(document.getElementById('max').value)||0; i++){
  let x=Math.floor((i%cols)*(cellW+pad))
  let y=Math.floor(Math.floor(i/cols)*(cellH+pad))
  data.frames["frame_"+i]={x,y,w:cellW,h:cellH}
 }

 let blob=new Blob([JSON.stringify(data,null,2)],{type:"application/json"})
 let a=document.createElement("a")
 a.href=URL.createObjectURL(blob)
 a.download="spritesheet.json"
 a.click()
}

updateMaxImages()
</script>

</body>
</html>
