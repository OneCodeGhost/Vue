<template>
  <div id="app">
    <div class='text-parent'>
      <p v-text="title"></p>
    </div>

    <div class="todo">
      <div class="add">
        <input type='text' placeholder="添加任务至列表" v-model='newItem' v-on:keyup.enter=addNew() />
        <button @click=addNew()>添加</button>
      </div>
    <ul>
      <li v-for='item in items' v-bind:class={finish:item.isFinished} v-on:click=ToggleClick(item)>{{item.todo}}</li>
    </ul>
    </div>

  </div>
</template>

<script>
import Hello from './components/Hello'

export default {
  data(){
    return {
      title:'TodoList!',
      items:[

      ]
    }
  },
  methods:{
    ToggleClick:function(i){
      i.isFinished=!i.isFinished;
    },
    addNew:function(){
      this.items.push(
        {
          todo:this.newItem,
          isFinished:false
        }
      )
      this.newItem='';
    }
  }
}
</script>

<style>
*{
  margin:0;
  padding:0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.finish{
  text-decoration:line-through;
  color:#ccc;
}
.text-parent{
  height:200px;
  background-color:#ccc;
}
p{
  position:relative;
  font-size:3em;
  font-weight:bold;
  top:50%;
  left:-20%;
  transform:translateY(-50%);
}
.add{
  display:flex;
  align-item:center;
}
.todo{
  position:relative;
  margin-top:25px;
  width:300px;
  left:25%;
  transform:translateX(-25%);
}
.add>input{
  border-radius:2px;
  border:1px solid #ccc;
  padding:2px 6px;
  line-height:16px;
  width:60%;
  font-size:10px;
}
::placeholder{
  color:#D7D7D7;
}
.add>button{
  width:20%;
  margin-left:0.4em;
  background-color:#42B983;
  border-radius:4px;
  border:0;
  color:#fff;
  font-size:12px;
  line-height:26px;
  outline:none;
}
ul{
  margin-top:30px;
  position:relative;
  left:10%;
  list-style:none;
}
li{
  font-size:24px;
  text-align:left;
}
</style>
