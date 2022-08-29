
<template>
  <diV>
  <p> Your score: {{ score }} ms</p>
  <p id="last">{{ finalR }}</p>
  </diV>
</template>

<script>
export default {
props: ['score','finalR']
}
</script>

<style>
#last{
  font-size: 24px;
  color: #4DB6AC;
  font-weight: bolder;
}
</style>