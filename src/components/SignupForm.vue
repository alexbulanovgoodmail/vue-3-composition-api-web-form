<script setup>
import { ref } from 'vue'

const email = ref('')
const password = ref('')
const role = ref('designer')
const terms = ref(true)
const names = ref([])
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

    <div class="terms">
      <input v-model="terms" type="checkbox" required />
      <label>Accept terms and conditions</label>
    </div>

    <div>
      <input v-model="names" value="Alex" type="checkbox" />
      <label>Alex</label>
    </div>
    <div>
      <input v-model="names" value="Tom" type="checkbox" />
      <label>Tom</label>
    </div>
    <div>
      <input v-model="names" value="Robin" type="checkbox" />
      <label>Robin</label>
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
</style>
