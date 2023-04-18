<script setup>
import { ref } from 'vue'

const email = ref('')
const password = ref('')
const role = ref('designer')
</script>

<template>
  <form>
    <label>Email:</label>
    <input v-model="email" type="email" required />

    <label>Password:</label>
    <input v-model="password" type="password" required />

    <label>Role:</label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>
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
</style>
