# Projeto-Java1

esse e o meu projeto de javascript do curso alura


let xbolinha = 300;
let ybolinha = 200;
let diametro = 15;
let raio = diametro / 2;

let velocidadexbolinha = 6;
let velocidadeybolinha = 6;
let raqueteconprimento = 10;
let raquetealtura = 90;


let xraquete = 5;
let yraquete = 150;

let xraqueteoponente = 585;
let yraqueteoponente = 150;
let velocidadeyoponente;

let colidiu = false 

let meuspontos = 0;
let pontosoponente = 0 

let raquetada;
let ponto;
let trilha;

function preload(){
  trilha = loadsound("trilha.mp3");
  ponto = loadsound ("ponto.mp3");
  raquetada = loadsound("raquetada.mp3");
  
  
  
}




function setup() {
  createCanvas(600, 400);
  trilha.loop();
}

function draw() {
  background(0);
  mostrabolinha();
  movimentaboliha();
  verificacolisaobolinha();
  mostraraquete(xraquete , yraquete);
  movimentaminharaquete();
  verificacolisaoraquete(xraqueteoponente,yraqueteoponente);
  incluiplacar();
  marcaponto();
}

function mostrabolinha(){
  circle(xbolinha,ybolinha,diametro);
}

function movimentabolinha(){
  xbolinha += velocidadexbolinha;
  ybolinha += velocidadeybolinha;

}

function verificacolisaoborda(){
  if (xbolinha + raio> width ||
     xbolinha - raio <3){
    velocidadexbolinha *= -1;
  }
   if (ybolinha + raio> height ||
      ybolinha - raio<3){
     velocidadeybolinha *= -1;
   }
}

function mostraraquete (x,y){
  rect(x , y, raquetecomprimento,)
}

function movimentaminharaquete(){
  if (keyisdown(UP_ARROW)){
    yraquete -= 10;
  }
  if (keyisdown(DOWN_ARROW)){
    yraquete += 10;
  
  }
}


function verificacolisaoraquete(){
  if (xbolinha - raio < xraquete + raquetecomprimento
     & ybolinha - raio < yraquete + raquetealtura&& ybolinha +
     raio > yraquete){
    velocidadexbolinha *= -1;
    raquete.play();
  }
}

function verificacolisaoraquete(x,y){
  colidiu =
    collidereactcircle(x,y,raquetecomprimento,raquetealtura,xbolinha,ybolinha,raio);
  if (collidiu){
    velocidadexbolinha *= -1;
  }
}

function movimentaraqueteoponente(){
    if (keyIsDown (87)){
      yraqueteoponente -=10;
    }
  if (keyIsDown (83)){
    yraqueteoponente +=10;
  }
}

function incluirplacar(){
  stroke(255);
  textAlign(CENTER);
  textSize(16);
  fill(color(255,140,0));
  rect(150,10,40,20);
  fill(255);
  text (meuspontos, 170,26);
  fill(color(255,140,0));
  rect(450,10,40,20);
  fill(255);
  text(pontosdooponente,470,26)
}

function marcaponto(){
  if (xbolinha > 590){
    meuspontos += 1;
    ponto.play();
  }
  if (ybolinha < 10){
    pontosdooponente += 1;
    ponto.play();
  }
}
