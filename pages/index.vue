<template>
<div>
  <div class="box" ref="boxA">
    <ul>
      <li class="con" v-for = "x in dataA" :key="x.id"
      @mousedown="mousedown($event, x.id)"
      @mouseup="mouseup($event, x.id, 'a')"
      @mousemove="mousemove($event, x.id)"
      :class="active == x.id ? 'active' : ''"
      :style="x.id == active" >
        
        {{x.text}}
      </li>
    </ul>
    
  </div>
  <div class="box" ref="boxB">
    <ul>
      <li class="con" v-for = "x in dataB" :key="x.id">
        
        {{x.text}}
      </li>
    </ul>
    
  </div>
</div>
</template>

<script>
export default {
  data(){
    return{
      dataA :[
        {id:1, text:"111"},
        {id:2, text:"222"},
        {id:3, text:"333"},
      ],
       dataB :[
        {id:4, text:"444"},
        {id:5, text:"555"},
        {id:6, text:"666"},
      ],
       active:null,
       boxA: {
         minX:0,
         maxX:0,
         minY:0,
         maxY:0
       },
       boxB: {
         minX:0,
         maxX:0,
         minY:0,
         maxY:0
       },
       initX:null,
       initY:null,
       transX:0,
       transY:0
    }
   
  },
  methods: {
    mousedown(e, id){
      console.log(e, id);
      this.active=id;
      this.initX = e.X;
      console.log(this.active);
    },
    mousemove(e, id){
      if(id ==this.active){
        console.log(e.x, e.y)
        this.transX = e.x - this.initX
      }
    },
    mouseup(e, id, box){
      this.active=null;
      this.initX=null;

    }
  }
  


}

</script>

<style>
.box {
 float: left;
 height: 400px;
 width: 200px;
 background-color: #4169e1;
 margin-left: 20px;
 margin-top:20px;
 
 
}
.con {
  background-color:ivory;
  margin-bottom: 10px;
  margin-top: 20px;
  padding: 5px;
  margin-right: 40px;

  
}
ul{
  list-style: none;
  text-align: center;
  
}

</style>
