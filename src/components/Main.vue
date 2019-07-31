<template>
    

<div class="calutor">
<div class="disply">{{count || '0'}}</div>
<div @click="clear" class="btn">C</div>
<div @click="singplus" class="btn">+/-</div>
<div @click="taqsim" class="btn">%</div>
<div @click="divide" class="btn opraitor">/</div>
<div @click="append('7')" class="btn">7</div>
<div @click="append('8')" class="btn">8</div>
<div @click="append('9')" class="btn">9</div>
<div @click="items" class="btn opraitor">x</div>
<div @click="append('4')" class="btn">4</div>
<div @click="append('5')" class="btn">5</div>
<div @click="append('6')" class="btn">6</div>
<div @click="maines" class="btn opraitor">-</div>
<div @click="append('1')" class="btn">1</div>
<div @click="append('2')" class="btn">2</div>
<div @click="append('3')" class="btn">3</div>
<div @click="add" class="btn opraitor">+</div>
<div @click="append('0')" class="btn ziro">0</div>
<div @click="dot" class="btn">.</div>
<div @click="mataa" class="btn opraitor">=</div>
</div>

</template>

<script>
export default {
  
data(){
return{
    pervious:null,
count:'',
opraitor:null,
operatorClicked:false,
}

},
methods:{

clear(){
this.count = '';

},
singplus(){
this.count = this.count.charAt(0)=== '-' ?
this.count.slice(1): `-${this.count}`;

},
taqsim(){
this.count = `${parseFloat(this.count)/100}`


},
append(number){
if(this.operatorClicked){
this.count = '';
this.operatorClicked = false;
}

this.count = `${this.count}${number}`;

},
dot(){
if(this.count.indexOf('.') === -1){

this.append('.');
}

},

setpervious(){

this.pervious = this.count;
this.operatorClicked = true;

},

divide(){
this.opraitor = (a,b) => a / b;
this.setpervious();
},
items(){

this.opraitor = (a,b) => a * b;
this.setpervious();

},
maines(){

this.opraitor = (a,b) => a - b;
this.setpervious();
},

add(){

this.opraitor = (a,b) => a + b;
this.setpervious();


},
mataa(){

this.count = `${this.opraitor(
parseFloat(this.count),
parseFloat(this.pervious)

)}`;
this.pervious = null;

}


}

}
</script>
<style>
.calutor{
width: 30%;
margin: auto;
display: grid;
grid-template-columns: repeat(4,1fr);
grid-auto-rows: minmax(50px,auto);

}
.disply{
grid-column: 1/5;
background-color: #333;
color: white;
font-size: 25px;
}
.ziro{
grid-column: 1/3;

}
.btn{
background-color: #eee;
font-size: 25px;
border: solid 1px #999;
}
.opraitor{
background-color: darkorange;
color: white;
}
</style>
