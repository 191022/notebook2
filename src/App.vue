<template>
  <div id="app" class="noteApp">
    <h1>记事本应用</h1>
    <my-note v-for="(note,index) in noteArry" :key="note.id" :note="note" :index="index" @delete="deleteMyNote"></my-note>
    <button @click="add" class="addButton">添加新笔记</button>
    <button @click="clean" class="cleanButton">清空所有笔记</button>
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  </div>
</template>

<script>
import myNote from './components/myNote.vue';
// import HelloWorld from './components/HelloWorld.vue'


export default {
  name: 'App',
  components: {
    myNote
    // HelloWorld,
  },
  data(){
    return{
      noteArry:[],
    };
  },
  created(){
    this.loadNote();
  },
  methods:{
    add:function(){
      const newNote={
        id:Date.now(),
        content:"",
      };
      this.noteArry.push(newNote);
    },
    clean:function(){
      localStorage.clear();
      this.noteArry=[];
    },
    deleteMyNote:function(index){
      const deleteNote=this.noteArry[index];
      localStorage.removeItem(deleteNote.id.toString());
      this.noteArry.splice(index,1);
    },
    loadNote:function(){
      for(let i=0;i<localStorage.length;i++){
        const key=localStorage.key(i);
        const content=localStorage.getItem(key);
        this.noteArry.push({
          id:parseInt(key),
          content: content,
        })
      }
    }
  }

};
</script>

<style scoped>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
body{
  font-family: sans-serif;
  background-color: rgb(216, 216, 216);
  margin: 0;
  padding: 20px;
}
h1{
  text-align: center;
  color: black;
  margin-top: 0;
}
.noteApp{
  max-width: 600px;
  margin: 0 auto;
  background-color: white;
  box-shadow: 0 0 10px gainsboro;
  border-radius: 5px;
  overflow: hidden;

}
.addButton{
  width: 100%;
  padding: 5px;
  font-size: 18px;
  margin-top: 20px;
  display: block;
  justify-content: center;
  align-items: center;
  text-align: center;
  border: 0;
  border-radius: 5px;
  color: rgb(244, 242, 242);
  background-color: rgb(130, 217, 188);

}
.cleanButton{
  width: 100%;
  padding: 5px;
  font-size: 18px;
  margin-top: 20px;
  display: block;
  justify-content: center;
  align-items: center;
  text-align: center;
  border: 0;
  border-radius: 5px;
  color: rgb(244, 242, 242);
  background-color: rgb(127, 127, 255);
  
}
</style>
