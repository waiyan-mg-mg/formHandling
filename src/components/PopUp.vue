<template>
  <div class="popUp">
    <div class="box">
      <div class="body">
        <p>Success <span style="color: lightgreen">✔</span></p>
      </div>
      <div class="footer">
        <button @click="hideBox">OK</button>
      </div>
    </div>
    <section class="overlay">&nbsp;</section>
  </div>
</template>

<script>
export default {
  name: "PopUp",
  data() {
    return {};
  },
  props: ["displayPopUp"],
  methods: {
    hideBox() {},
  },
};
</script>

<style scoped>
.popUp {
  position: absolute;
  left: 50%;
  top: 40%;
  transform: translate(-50%, -50%);
}
.overlay {
  position: absolute;
  top: -95px;
  left: -600px;
  width: 300vw;
  height: 120vh;
  background: rgba(156, 156, 156, 0.363);
  z-index: -1;
}
.box {
  width: 400px;
  height: 200px;
  margin: 20vh auto;
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
