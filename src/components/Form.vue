<template>
  <h1>{{ email }}</h1>
  <h1>{{ password }}</h1>
  <h1>{{ role }}</h1>
  <form>
    <div class="email">
      <label for="email">Email</label>
      <input type="text" id="email" v-model="email" />
    </div>
    <div class="password">
      <label for="password">password</label>
      <input type="password" id="password" v-model="password" />
    </div>
    <div class="role">
      <label for="password">Role :</label>
      <select v-model="role">
        <option value="editor">Page Editor</option>
        <option value="Owner">Page Owner</option>
        <option value="admin">Page Admin</option>
        <option value="content">Content Writer</option>
      </select>
    </div>
  </form>
</template>

<script>
export default {
  name: "FormBox",
  data() {
    return {
      email: null,
      password: null,
      role: null,
    };
  },
  methods: {},
};
</script>
<style>
form {
  max-width: 500px;
  margin: 10vh auto;
  padding: 30px;
  border-radius: 10px;
  background: white;
  font-size: 1.4rem;
}
label {
  display: block;
  margin: 10px 0;
}
input,
select,
button {
  width: 100%;
  height: 30px;
  border: none;
  border-bottom: 2px solid rgba(0, 0, 0, 0.637);
  font-size: 1.6rem;
  caret-color: rgb(255, 0, 0);
  font-family: "Courier New", Courier, monospace;
  font-weight: bold;
  padding-left: 2px;
}
select {
  outline: 2px solid rgb(9, 255, 0);
}
input:focus {
  border-bottom: 2px solid rgb(9, 255, 0);
}
/* .email {
  transition: all 300ms;
}
.email:hover {
  transform: translateY(-20px);
  background: rgb(221, 221, 221);
  padding: 10px;
  border-radius: 8px;
}
.email:hover input {
  border-radius: 5px;
} */
</style>
