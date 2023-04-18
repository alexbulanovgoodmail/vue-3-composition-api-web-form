<script setup>
import { handleError, ref } from 'vue'

const email = ref('')
const password = ref('')
const passwordError = ref('')
const role = ref('designer')
const terms = ref(true)
const tempSkill = ref('')
const skills = ref([])

// methods
function addSkill(e) {
  if (e.key === ',' && tempSkill.value) {
    if (!skills.value.includes(tempSkill.value)) {
      skills.value.push(tempSkill.value)
    }
    tempSkill.value = ''
  }
}

function deleteSkill(index) {
  skills.value.splice(index, 1)
}

function handleSubmit(params) {
  // validate password
  passwordError.value = password.value.length > 5 ? '' : 'Password must be at least 6 chars long'

  if (!passwordError.value) {
    console.log('email', email.value)
    console.log('password', password.value)
    console.log('role', role.value)
    console.log('skills', skills.value)
    console.log('terms accepted', terms.value)
  }
}
</script>

<template>
  <form @submit.prevent="handleSubmit">
    <label>Email:</label>
    <input v-model="email" type="email" required />

    <label>Password:</label>
    <input v-model="password" type="password" required />
    <div v-if="passwordError" class="error-text">
      {{ passwordError }}
    </div>

    <label>Role:</label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>

    <label>Skills:</label>
    <input v-model="tempSkill" type="text" @keyup.alt="addSkill" />
    <div class="skills">
      <div v-for="(skill, index) in skills" :key="index" class="skill" @click="deleteSkill(index)">
        {{ skill }}
      </div>
    </div>

    <div class="terms">
      <input v-model="terms" type="checkbox" required />
      <label>Accept terms and conditions</label>
    </div>

    <div class="submit">
      <button type="submit">Create an Account</button>
    </div>
  </form>
</template>

<style scoped>
form {
  margin: 30px auto;
  border-radius: 10px;
  max-width: 420px;
  padding: 40px;
  text-align: left;
  background-color: #ffffff;
}

label {
  margin: 25px 0 15px;
  display: inline-block;
  font-size: 0.6em;
  font-weight: bold;
  text-transform: uppercase;
  letter-spacing: 1px;
  color: #aaaaaa;
}

input,
select {
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #dddddd;
  display: block;
  width: 100%;
  padding: 10px 6px;
  color: #555555;
}

input[type='checkbox'] {
  position: relative;
  top: 2px;
  margin: 0 10px 0 0;
  display: inline-block;
  width: 16px;
}

button {
  border: 0;
  border-radius: 8px;
  padding: 10px 20px;
  color: #ffffff;
  background-color: #0b6dff;
  cursor: pointer;
}

.skills {
  margin: 4px -4px;
  display: flex;
  flex-wrap: wrap;
}

.skill {
  margin: 4px;
  border-radius: 8px;
  padding: 6px 12px;
  font-size: 24px;
  font-family: monospace;
  font-weight: bold;
  color: #777777;
  background-color: #eee;
  cursor: pointer;
  transition: color 0.6s;
}

.skill:hover {
  color: initial;
}

.submit {
  margin-top: 20px;
  text-align: center;
}

.error-text {
  margin-top: 4px;
  font-family: monospace;
  font-size: 0.8em;
  font-weight: bold;
  color: #ff0000;
}
</style>
