<template>
   <div v-if="togglePopup">
      <PopUp @closePopUp='closePopUp' /> 
   </div>
  <form @submit.prevent="submit">
    <div class="email">
      <label for="email">Email</label>
      <input type="text" id="email" v-model="email" />
    </div>
    <p class="errorMsg" v-if="emailValid">Email must have @ and . sign</p>
    <div class="password">
      <label for="password">Password</label>
      <input type="password" id="password" v-model="password" />
    </div>
    <p class="errorMsg" v-if="passwordValid">
      Passwrod must be at least 8 charactors.
    </p>
    <div class="role">
      <label for="password">Role :</label>
      <select v-model="role">
        <option value="editor">Page Editor</option>
        <option value="Owner">Page Owner</option>
        <option value="admin">Page Admin</option>
        <option value="content">Content Writer</option>
      </select>
    </div>
    <div class="skills">
      <label for="skills"
        >Skills
        <span
          >'Press Enter to jump next skill and ^ to clear skills'</span
        ></label
      >
      <input
        type="text"
        id="skills"
        @focus="hideSkill"
        @keyup="collectSkills"
        @blur="showSkills"
        v-model="skillCounter"
      />
    </div>
    <div class="learned">
      <label for="learned">I've also learned</label><br />
      <input
        type="checkbox"
        id="computerScience"
        value="computerScience"
        v-model="learned"
      /><label for="computerScience">Computer Science</label><br />
      <input
        type="checkbox"
        id="accounting"
        value="accounting"
        v-model="learned"
      /><label for="accounting">Accounting</label><br />
      <input
        type="checkbox"
        id="cyberSecurity"
        value="cyberSecurity"
        v-model="learned"
      /><label for="cyberSecurity">Cyber Security</label><br />
    </div>
    <br />
    <hr />
    <div class="privacy">
      <input type="checkbox" id="terms" v-model="terms" />
      <label for="terms">Accept terms and conditions</label>
    </div>
    <p class="errorMsg" v-if="termValid">
      You must need to accept terms and conditions.
    </p>
    <div class="submit">
      <button type="submit" @click="toggleSuccess">Next</button>
    </div>
  </form>
</template>

<script>
import PopUp from "./PopUp.vue";

export default {
  name: "FormBox",
  components: { PopUp },
  data() {
    return {
      email: "",
      password: "",
      role: "Owner",
      terms: '',
      learned: [],
      skills: [],
      skillCounter: "",
      emailValid: false,
      passwordValid: false,
      termValid: false,
      togglePopup:false
    };
  },
  methods: {
    collectSkills(e) {
      if (e.key === "Enter") {
        this.skills.push(this.skillCounter);
        this.skillCounter = "";
      } else if (e.key === "^") {
        if (this.skills.length === 0) {
          alert("nothing to clean");
          this.skillCounter = "";
        } else {
          let confirm = window.confirm(
            `Are you sure to clean "${this.skills}"`
          );
          if (confirm) {
            this.skills = [];
            this.skillCounter = "";
          } else this.skillCounter = "";
        }
      }
    },
    showSkills() {
      this.skillCounter = this.skills;
    },
    hideSkill() {
      this.skillCounter = "";
    },
    submit() {
      !this.terms ? (this.termValid = true) : (this.termValid = false); // for terms
      !this.email.includes("@") || !this.email.includes(".")
        ? (this.emailValid = true)
        : (this.emailValid = false); // for email
      this.password.length < 8
        ? (this.passwordValid = true)
        : (this.passwordValid = false); // for password
    },
    toggleSuccess() { 
        this.togglePopup = true;
    },
    closePopUp(){
      this.togglePopup=false;
    }
  },
};
</script>
<style scoped>
header {
  text-align: center;
}
form {
  max-width: 500px;
  margin: 10vh auto;
  padding: 30px;
  border-radius: 10px;
  background: white;
  font-size: 1.4rem;
  box-shadow: 1px 3px 10px rgb(168, 168, 168);
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
  outline: none;
  background: rgb(97, 96, 96);
  color: white;
  border-radius: 5px;
}
input:focus {
  border-bottom: 2px solid rgb(9, 255, 0);
}
div.skills input:focus {
  border: 2px dashed gray;
  padding: 20px;
  font-size: 1.3rem;
}
div.skills span {
  font-size: 1rem;
}
.privacy {
  padding-top: 30px;
}
input[type="checkbox"] {
  display: inline-block;
  width: 20px;
  height: 20px;
  margin: 0 10px 0 0;
}
label[for="terms"] {
  display: inline;
  margin: 0;
}
div.learned {
  padding-top: 20px;
}
div.learned label {
  display: inline;
}
div.submit {
  text-align: center;
  margin-top: 20px;
}
div.submit button {
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  width: auto;
  height: auto;
  border-radius: 6px;
  background: deepskyblue;
  color: white;
  padding: 10px;
  outline: none;
  border: none;
  cursor: pointer;
}
p.errorMsg {
  color: crimson;
  font-size: 1.2rem;
  font-style: italic;
}
</style>
