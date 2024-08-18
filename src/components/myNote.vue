<template>
    <div class="note">
        <div class="writeNote">
            <textarea v-model="note.content" placeholder="请在此书写你的笔记....."></textarea>
        </div>
        <div class="deleteNote">
            <button @click="deleteMyNote">删除</button>
        </div>
    </div>
</template>

<script>
export default {
    props:{
        note:Object,
        index:Number,
    },
    watch:{
        "note.content": function(newcontent){
            this.save();
        },
    },
    methods:{
        deleteMyNote:function(){
            this.$emit("delete",this.index);
        },
        save:function(){
            localStorage.setItem(this.note.id.toString(),this.note.content)
        }
    },

};
</script>

<style scoped>
.note{
    margin: 0 auto;
    margin-bottom: 5px;
    padding: 5px;
    border: 1px solid rgb(228, 228, 228);
    border-radius: 5px;
}
.writeNote textarea{
    width: 100%;
    height: 100px;
    border:0;
    background-color: rgb(246, 245, 245);
}
.deleteNote button{
    border: 0;
    border-radius: 5px;
    background-color:rgb(243, 152, 152);
    color: rgb(252, 252, 253);
    font: 1em sans-serif;
    text-align: center;
    display: block;
    padding: 5px;
    font-size: 16px;
    margin-top: 5px;
    justify-content: center;
    align-items: center;
}
</style>

