<template>
<body>
  <div id="timer">
        <div class="box">
            <div id="h" class="time">00</div>
            <div class="boxMao">:</div>
            <div id="m" class="time">00</div>
            <div class="boxMao">:</div>
            <div id="s" class="time">00</div>
        </div>
        <div class="timeButton">
            <button @click="start"></button>
            <button @click="pause">停止</button>
            <button @click="reset">重置</button>
        </div>
    </div>
</body>
  
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
body{
    display:flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: auto;
    background-color: rgb(246, 242, 242);
}
#timer{
    display:flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.time {
    padding: 10px 25px;
    background-color: #fff;
    border-radius: 5px;
    margin: 0 10px;
    box-shadow: 0 2px 5px rgb(228, 227, 227);
    justify-content: center;
    align-items: center;
}

.box {
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 80px;
    color: rgb(0, 0, 0);
    margin-bottom: 40px;
}

.boxMao {
    margin: 0 auto;
    justify-content: center;
    align-items: center;
}

.timeButton {
    display: flex;
    flex-direction: row;
    align-items: center;
}

.timeButton button {
    font-size: 20px;
    padding: 20px 40px;
    border: 0;
    color: #fff;
    background-color: rgb(105, 105, 235);
    margin: 10px 20px;
    border-radius: 5px;
    justify-content: center;
    align-items: center;
}
button:hover{
    background-color: rgb(170, 165, 247);
}
</style>
