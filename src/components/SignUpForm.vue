<template>
  <form>
    <label>Email</label>
    <input type="email" required v-model="email" />

    <label>Password</label>
    <input type="password" required v-model="password" />

    <label>Role:</label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>


    <label>Skills</label>
    <input type="text" v-model="tempSkill" @keyup.alt="addSkill">

    <div v-for="skill in skills" :key="skill" class="pill">
        {{ skill }}
    </div>

    <!-- Two-way Data Binding a single checkbox to a boolean property -->
    <div class="terms">
        <input type="checkbox" required v-model="terms">
        <label>Accept terms and conditions</label>
    </div>
    
    <!-- Two-way Data binding multiple checkboxes to an array property -->
    <div>
        <input type="checkbox" v-model="names" value="shaun">
        <label>John</label>

        <input type="checkbox" v-model="names" value="yoshi">
        <label>Yoshi</label>

        <input type="checkbox" v-model="names" value="mario">
        <label>Mario</label>
    </div>
  </form>

  <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Role: {{ role }} </p>
  <p>Terms Accepted: {{ terms }}</p>
  <p>Names: {{ names }}</p>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: 'designer',
      terms: false,
      names: [],
      tempSkill: "",
      skills: [],
    };
  },
  
  methods: {
    addSkill(e) {
        console.log(e);
        //if the key pressed is a comma and the tempSkill property is not empty
        if (e.key === ',' && this.tempSkill) {
            if (!this.skills.includes(this.tempSkill)) {
                this.skills.push(this.tempSkill);
            }
            this.tempSkill = '';
        }
    }
  }
};
</script>

<style>
form {
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}

label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}

input, select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}

input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
}
</style>