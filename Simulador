<!doctype html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Simulador avanzado de mezclas de tintes</title>

<style>
body{
  font-family: Arial, sans-serif;
  background:#f4f4f4;
  padding:12px;
}
.contenedor{
  max-width:560px;
  background:#fff;
  margin:auto;
  padding:16px;
  border-radius:10px;
  box-shadow:0 0 8px rgba(0,0,0,.1);
}
h2{text-align:center;margin-top:0}
label{font-weight:bold;margin-top:10px;display:block}
select,button{
  width:100%;
  padding:8px;
  margin-top:6px;
  font-size:16px;
}
button{
  background:#2a7ae2;
  color:#fff;
  border:none;
  border-radius:6px;
}
.resultado{
  margin-top:14px;
  padding:12px;
  border:1px solid #ccc;
  border-radius:8px;
  background:#fafafa;
  white-space:pre-line;
}
.nota{
  font-size:13px;
  color:#555;
  margin-top:10px;
}
</style>
</head>

<body>

<div class="contenedor">
<h2>Simulador avanzado de mezcla de tintes</h2>

<label>Base A</label>
<select id="baseA"></select>

<label>Base B</label>
<select id="baseB"></select>

<label>Oxidante</label>
<select id="oxidante">
  <option value="10">10 vol</option>
  <option value="20" selected>20 vol</option>
  <option value="30">30 vol</option>
</select>

<label>Ratio de mezcla</label>
<select id="ratio">
  <option value="1">1 : 1</option>
  <option value="1.5">1 : 1,5</option>
</select>

<label>Porcentaje de canas</label>
<select id="canas">
  <option value="0">0 %</option>
  <option value="25">25 %</option>
  <option value="50">50 %</option>
  <option value="75">75 %</option>
  <option value="100">100 %</option>
</select>

<button onclick="mezclar()">Mezclar</button>

<div class="resultado" id="resultado">
Selecciona las opciones para ver el resultado
</div>

<div class="nota">
Simulación orientativa para formación profesional en peluquería.
</div>
</div>

<script>
const reflejos = [
  "Natural","Ceniza","Iris","Dorado",
  "Cobrizo","Caoba","Violeta","Beige"
];

const complementarios = {
  1:"Dorado", 3:"Ceniza",
  4:"Ceniza", 6:"Dorado"
};

const baseA=document.getElementById("baseA");
const baseB=document.getElementById("baseB");

for(let n=1;n<=10;n++){
  for(let r=0;r<reflejos.length;r++){
    const txt=n+"."+r+" – "+reflejos[r];
    baseA.add(new Option(txt,n+"."+r));
    baseB.add(new Option(txt,n+"."+r));
  }
}

function mezclar(){
  const A=baseA.value.split(".");
  const B=baseB.value.split(".");
  const ox=parseInt(document.getElementById("oxidante").value);
  const ratio=parseFloat(document.getElementById("ratio").value);
  const canas=parseInt(document.getElementById("canas").value);

  let nivel=(+A[0]+ +B[0])/2;
  if(ox===20) nivel+=1;
  if(ox===30) nivel+=2;

  let reflejoFinal;
  if(A[1]===B[1]){
    reflejoFinal=reflejos[A[1]];
  }else{
    reflejoFinal=reflejos[A[1]]+" / "+reflejos[B[1]];
  }

  let notaCanas="";
  if(canas>=50){
    notaCanas="\n⚠ Aconsejable aumentar base natural (.0)";
  }

  let neutralizacion="";
  if(complementarios[A[1]]){
    neutralizacion="\nNeutraliza: "+complementarios[A[1]];
  }

  document.getElementById("resultado").textContent=
    "Nivel aproximado: "+nivel.toFixed(1)+
    "\nReflejo: "+reflejoFinal+
    "\nRatio: 1 : "+ratio+
    "\nCanas: "+canas+" %"+
    neutralizacion+
    notaCanas;
}
</script>

</body>
</html>
