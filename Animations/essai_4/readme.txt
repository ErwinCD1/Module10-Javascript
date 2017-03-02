Utilisation de la camera dans un navigateur-------------------------------------------
Url     : http://codes-sources.commentcamarche.net/source/54748-utilisation-de-la-camera-dans-un-navigateurAuteur  : kazmaDate    : 07/08/2013
Licence :
=========

Ce document intitulé « Utilisation de la camera dans un navigateur » issu de CommentCaMarche
(codes-sources.commentcamarche.net) est mis à disposition sous les termes de
la licence Creative Commons. Vous pouvez copier, modifier des copies de cette
source, dans les conditions fixées par la licence, tant que cette note
apparaît clairement.

Description :
=============

suite a des testes sur l'utilisation d'une webcam dans un navigateur je me suis 
amus&eacute; a cr&eacute;&eacute; cette source qui est un m&eacute;lange de java
script css3d canvas  et bien entendu de l'api getUserMedia() pour la gestion de 
la webcam
<br />
<br />compatible avec les toutes derni&egrave;res versions de
 firefox chrome pour ce dernier le teste est a faire en ligne, fonctionne aussi 
avec opera mais sans le cube car opera ne supporte pas encore le css3d
<br />

<br />je rajoute un lien pour tester le tout (il faudra retirer les espace dans 
le lien)
<br />
<br /><a href='http://scriptevol.toile-libre.org/scriptsite/cu
becam.html' target='_blank'>http://scriptevol.toile-libre.org/scriptsite/cubecam
.html</a>
<br /><a name='source-exemple'></a><h2> Source / Exemple : </h2>
<b
r /><pre class='code' data-mode='basic'>
var kcubecam={

vaval:0,
vavam:0,

inter:null,
a:0,
tbm:new Array,

azerty:function(sens){

		var elem=docume
nt.getElementById(&quot;cube&quot;);

		if(sens=='droite'){
			this.vaval+=45

			elem.style.WebkitTransform='rotateX('+this.vavam+'deg) rotateY('+this.vaval
+'deg)';
			elem.style.MozTransform='rotateX('+this.vavam+'deg) rotateY('+this.
vaval+'deg)';
		}

		if(sens=='gauche'){
			this.vaval-=45;
			elem.style.W
ebkitTransform='rotateX('+this.vavam+'deg) rotateY('+this.vaval+'deg)';
			elem
.style.MozTransform='rotateX('+this.vavam+'deg) rotateY('+this.vaval+'deg)';
		
}

		if(sens=='haut'){
			this.vavam+=45;
			elem.style.WebkitTransform='rot
ateX('+this.vavam+'deg) rotateY('+this.vaval+'deg)';
			elem.style.MozTransform
='rotateX('+this.vavam+'deg) rotateY('+this.vaval+'deg)';
		}

		if(sens=='ba
s'){
			this.vavam-=45;
			elem.style.WebkitTransform='rotateX('+this.vavam+'d
eg) rotateY('+this.vaval+'deg)';
			elem.style.MozTransform='rotateX('+this.vav
am+'deg) rotateY('+this.vaval+'deg)';
		}

	},

	clone0:function(){

	var
 vivi = document.getElementById('sourcevid');

	var moncanvas2=document.create
Element('canvas');
	moncanvas2.width=50;
	moncanvas2.height=50;
	var moncanva
s2d=moncanvas2.getContext('2d');
	moncanvas2d.drawImage(vivi,0,0,50,50);
	
	i
f(kcubecam.tbm.length==0){
		for(var i=0;i&lt;100;i++){
			kcubecam.tbm.push(m
oncanvas2d.getImageData( 0, 0, 50, 50));
		}
	}
	
	kcubecam.tbm.unshift(monc
anvas2d.getImageData( 0, 0, 50, 50));
	kcubecam.tbm.pop();
	
	var can = docum
ent.getElementById('fond');
	var canvas1 = document.getElementById('fond').getC
ontext('2d');
	
	for(var i=0;i&lt;10;i++){
		
		for(var j=0;j&lt;10;j++){
	
		
			canvas1.putImageData(kcubecam.tbm[(i*10)+j],j*50,i*50);
			
		}
	}
	k
cubecam.copie(can)
},

clone1:function(){

	var vivi = document.getElementB
yId('sourcevid');
	var can = document.getElementById('fond');
	var canvas1 = c
an.getContext('2d');
	
	kcubecam.a &gt;= Math.PI*2 ? kcubecam.a=0 : null;
	

	for(var i=50;i&lt;=500;i+=50){
		
		for(var j=50;j&lt;=500;j+=50){
			
			c
anvas1.save();
			canvas1.translate(j-25,i-25);
			canvas1.rotate(kcubecam.a);

			canvas1.drawImage(vivi,-25,-25,50,50);
			canvas1.restore();
		}
	}
	kc
ubecam.copie(can);
	canvas1.drawImage(vivi,150,150,200,200);
	kcubecam.a+=Math
.PI/32;
	
},

clone2:function(){

	var vivi = document.getElementById('sou
rcevid');
	var can = document.getElementById('fond');
	var canvas1 = can.getCo
ntext('2d');
	
	var z=0;
	
	for(var i=50;i&lt;=500;i+=50){
		
		if (kcubec
am.a==3){
			kcubecam.a=1;
			var b=7
		}
		else{
			kcubecam.a=3;
			var 
b=5;
		}

		for(var j=50;j&lt;=500;j+=50){
			
			if (z==kcubecam.a){
				
z=b;
			}
			else{
				z=kcubecam.a;
			}
			canvas1.save();
			canvas1.tr
anslate(j-25,i-25);
			canvas1.rotate((Math.PI/8)*z*2);
			canvas1.drawImage(v
ivi,-25,-25,50,50);
			canvas1.restore();
		}
	}
	kcubecam.copie(can);
	
}
,

clone3:function(){

	var vivi = document.getElementById('sourcevid');
	v
ar can = document.getElementById('fond');
	var canvas1 = can.getContext('2d');

	
	for(var i=50;i&lt;=500;i+=50){
		
		kcubecam.a=0;
		for(var j=50;j&lt;=5
00;j+=50){
			
			if (kcubecam.a==2) {
				kcubecam.a=0;
			}
			canvas1.sa
ve();
			canvas1.translate(j-25,i-25);
			canvas1.rotate(Math.PI*kcubecam.a);

			canvas1.drawImage(vivi,-25,-25,50,50);
			kcubecam.a+=1/2;
			canvas1.rest
ore();
		}
	}
	kcubecam.copie(can);
	kcubecam.a=0;
},

clone4:function(){


	var vivi = document.getElementById('sourcevid');
	var can = document.getEl
ementById('fond');
	var canvas1 = can.getContext('2d');
	
	for(var i=50;i&lt;
=500;i+=50){
		
		for(var j=50;j&lt;=500;j+=50){
		
		if (kcubecam.a==2) {

		kcubecam.a=0;
		}
			canvas1.save()
			canvas1.translate(j-25,i-25);
			

			if(kcubecam.a==1 || kcubecam.a==0){
			canvas1.scale(-1,-1);
			}
			canva
s1.drawImage(vivi,-25,-25,50,50);
			kcubecam.a+=1/2;
			canvas1.restore();
	
	}
	}
	kcubecam.copie(can);
	kcubecam.a=0;
},

clone5:function(){

	var 
vivi = document.getElementById('sourcevid');
	var can = document.getElementById
('fond');
	var canvas1 = can.getContext('2d');
	
	for(var i=50;i&lt;=500;i+=5
0){
		
		for(var j=50;j&lt;=500;j+=50){
		
		if (kcubecam.a==2) {
		kcubeca
m.a=0;
		}
		
			canvas1.save();
			canvas1.translate(j-25,i-25)
			
			if
(kcubecam.a==1 || kcubecam.a==0){
			canvas1.scale(-1,1);
			}
			canvas1.dra
wImage(vivi,-25,-25,50,50);
			kcubecam.a+=1/2;
			canvas1.restore();
		}
	}

	kcubecam.copie(can);
	kcubecam.a=0;
},

clone6:function(){
	var vivi = d
ocument.getElementById('sourcevid');
	var can = document.getElementById('fond')
;
	var canvas1 = can.getContext('2d');
	
	for(var i=50;i&lt;=500;i+=50){
		

		for(var j=50;j&lt;=500;j+=50){
		
		if (kcubecam.a==2) {
		kcubecam.a=0;

		}
		
			canvas1.save();
			canvas1.translate(j-25,i-25)
			
			if(kcubeca
m.a==1 || kcubecam.a==0){
			canvas1.scale(1,-1);
			}
			canvas1.drawImage(v
ivi,-25,-25,50,50);
			kcubecam.a+=1/2;
			canvas1.restore();
		}
	}
	kcube
cam.copie(can);
	kcubecam.a=0;
},

clone7:function(){
	var vivi = document.
getElementById('sourcevid');
	var can = document.getElementById('fond');
	var 
canvas1 = can.getContext('2d');
	
	for(var i=50;i&lt;=500;i+=50){
		
		for(v
ar j=50;j&lt;=500;j+=50){
		
		if (kcubecam.a==2) {
		kcubecam.a=0;
		}
			
canvas1.save();
			canvas1.translate(j-25,i-25)
			
			if(kcubecam.a==0 || kc
ubecam.a==1.5){
			canvas1.scale(-1,1);
			}
			canvas1.drawImage(vivi,-25,-2
5,50,50);
			kcubecam.a+=1/2;
			canvas1.restore();
		}
	}
	kcubecam.copie(
can)
	kcubecam.a=0
},

clone8:function(){
	var vivi = document.getElementBy
Id('sourcevid');
	var can = document.getElementById('fond');
	var canvas1 = ca
n.getContext('2d');
	
	for(var i=50;i&lt;=500;i+=50){
	
		for(var j=50;j&lt;
=500;j+=50){
		
		if (kcubecam.a==2) {
		kcubecam.a=0;
		}
		
			canvas1.s
ave();
			canvas1.translate(j-25,i-25);
			
			if(kcubecam.a==1 || kcubecam.a
==1.5){
			canvas1.scale(1,-1);
			}
			canvas1.drawImage(vivi,-25,-25,50,50)
;
			kcubecam.a+=1/2;
			canvas1.restore();
		}
	}
	kcubecam.copie(can);
	
kcubecam.a=0;
},

copie:function(can){

	document.getElementById('droite').
getContext('2d').drawImage(can,0,0);
	document.getElementById('gauche').getCont
ext('2d').drawImage(can,0,0);
	document.getElementById('face').getContext('2d')
.drawImage(can,0,0);
	document.getElementById('dessus').getContext('2d').drawIm
age(can,0,0);
	document.getElementById('dessous').getContext('2d').drawImage(ca
n,0,0);
},
}

function dispatche(effet){

	clearInterval(kcubecam.inter);

	kcubecam.a=0;
	
	if (effet=='retard') {
		kcubecam.a=3;
		kcubecam.inter=s
etInterval(kcubecam.clone0,40);
	}

	if (effet=='rond') {
		kcubecam.a=3;
	
	kcubecam.inter=setInterval(kcubecam.clone1,40,kcubecam.a);
	}
	
	if (effet==
'carre') {
		kcubecam.inter=setInterval(kcubecam.clone2,40,kcubecam.a);
	}
	

	if (effet=='dr') {
		kcubecam.inter=setInterval(kcubecam.clone3,40,kcubecam.a
);
	}
	
		if (effet=='dz') {
		kcubecam.inter=setInterval(kcubecam.clone4,40
,kcubecam.a);
	}
	
		if (effet=='db') {
		kcubecam.inter=setInterval(kcubeca
m.clone5,40,kcubecam.a);
	}
	
	if (effet=='dc') {
		kcubecam.inter=setInterv
al(kcubecam.clone6,40,kcubecam.a);
	}
	
	if (effet=='dd') {
		kcubecam.inter
=setInterval(kcubecam.clone7,40,kcubecam.a);
	}
	
	if (effet=='de') {
		kcub
ecam.inter=setInterval(kcubecam.clone8,40,kcubecam.a);
	}
}

function init()
 {

	video = document.getElementById('sourcevid');
	
	if (navigator.getUserM
edia) {
		
		navigator.getUserMedia('video', successCallback, errorCallback);

		
		function successCallback(stream) {
			video.src = stream;
			video.play
();
		}
		function errorCallback(error) {
			alert('code erreur' + error.code
 + ']');
			return;
		}	
		
		
	}
	
	else if (navigator.mozGetUserMedia) 
{
		
		window.navigator.mozGetUserMedia({video:true},
		
		function (stream)
 {
			video.mozSrcObject = stream;
			video.play();
		},

		function (error
) {
			alert('code erreur' + error.code + ']');
			return;
		})
		
	}

	e
lse if (navigator.webkitGetUserMedia) {

		window.navigator.webkitGetUserMedia
({video: true},
		
		function (stream) {
			
			video.src = window.webkitURL
.createObjectURL(stream);
			video.play();
		},
		function (error) {
			aler
t('code erreur' + error.code + ']');
			return;
		})
	}
}

window.onload =
 init;
</pre>
<br /><a name='conclusion'></a><h2> Conclusion : </h2>
<br />t
out a fait
