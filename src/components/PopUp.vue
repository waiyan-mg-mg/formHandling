<template>
   <div class="overlay" @click.self="hideBox">
      <div class="box">
      <div class="body">
        <p>Success <span style="color: lightgreen">✔</span></p>
      </div>
      <div class="footer">
        <button @click="hideBox">OK</button>
      </div>
    </div>
   </div>
</template>

<script>
export default {
  name: "PopUp",
  data() {
    return {};
  },
  props: [],
  methods: {
    hideBox() {
      this.$emit('closePopUp')
    },
  },
};
</script>

<style scoped>
.overlay{
    position: absolute;
    width: 100vw;
    margin-top: -190px;
    height: 150%;
    background-color:rgba(70, 70, 70, 0.315);
    padding-top:20%;
}
.box {
  max-width: 400px;
  height: 200px;
  margin: 0 auto;
  background: deepskyblue;
  padding: 30px;
  border-radius: 15px;
}
.body {
  height: 50%;
  text-align: center;
}
.body p {
  color: white;
  font-size: 4rem;
}
.footer {
  height: 50%;
  text-align: right;
}
.footer button {
  margin-top: 40px;
  padding: 10px 20px;
  border-radius: 5px;
  font-weight: bold;
  border-color: white;
}
</style>
