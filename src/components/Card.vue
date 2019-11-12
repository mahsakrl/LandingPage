<template>
  <div class="card-box">
    <div class="card-img">
      <img src="../assets/images/icon-brand-recognition.svg" />
    </div>
    <div class="card-title">
      <h4>{{title}}</h4>
    </div>
    <div class="card-subtitle">
      <p>{{subTitle}}</p>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Card',
  props: {
    title: String,
    subTitle: String,
    image: String
  }
}
</script>
<style scoped lang="scss">
// @import url('../assets/styles/variable');
.card-box {
  width: 250px;
  height: 300px;
  background-color: white;
  border-radius: 6px;
}
h4 {
  font-size: 800;
}
.card-img {
  display: flex;
  width: 70px;
  height: 70px;
  border-radius: 35px;
  background-color: hsl(257, 27%, 26%);
  margin-top: -30px;
  align-items: center;
  justify-content: center;
  margin-left: 25px;
}
img {
  width: 40px;
  height: 40px;
}
h4 {
  text-align: left;
  padding-left: 25px;
}
.card-subtitle {
  padding-left: 25px;
  text-align: left;
  color: hsl(257, 7%, 63%);
}
@media screen and (min-width: 800px) {
  .card-img{
    margin-left: 35%;
  }
}
</style>
