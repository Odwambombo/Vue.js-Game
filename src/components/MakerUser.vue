<template>
  <div class="block" v-if="showMe" @click="StopTimer">
    Click Me
  </div>
</template>

<script>
export default {
props: ['delay'],
data(){
  return{
    showMe: false,
    timer: null,
    ReactiveTime: 0
  }
},
mounted(){
  console.log('Componenet mounted')
  setTimeout(()=> {
    this.showMe = true,
    this.startTimer(),
    console.log(this.delay)
  }, this.delay)
},

methods: {
  startTimer(){

    this.timer = setInterval(()=> {
      this.ReactiveTime += 10
    }, 10)
  },
  StopTimer(){
    clearInterval(this.timer)
    console.log(this.ReactiveTime)
    this.$emit('close', this.ReactiveTime)
  }
}

}
</script>

<style>
.block{
    justify-content: center;
    text-align: center;
    background-color: #4DB6AC;
    border-radius: 20px;
    padding: 100px 0;
    margin: 40px auto;
    width: 400px;
    font-weight: bold;
    
}
</style>