<template>
  <header>
    <div class="header-container"><h1>Simple Task</h1></div>
  </header>
  <main>
    <form>
      <label>Change the data:</label>
      <div class="input-data" v-for="(item, index) in arr" :key="index">
        <select v-model="selectedIndex" v-if="selectedIndex === index">
          <option v-for="(option, optionIndex) in arr" :value="optionIndex">
            {{ option.name }}
          </option>
        </select>
        <input type="text" v-model="item.value" v-if="selectedIndex === index" />
      </div>
    </form>
  </main>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue'
let arr = ref<{ name: string; value: string }[]>([])
let selectedIndex = ref(0)
let i = 0
while (i < 31) {
  let obj = {
    name: `boo${i}`,
    value: `foo${i}`
  }
  arr.value.push(obj)
  i++
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
  border: none;
  text-decoration: none;
}
h1,
h2,
h3,
p,
a,
span {
  margin: 0;
  padding: 0;
  text-decoration: none;
}
header {
  position: fixed;
  top: 0;
  height: 60px;
  width: 100%;
  display: grid;
  justify-items: center;
  margin-top: 10px;
}
.header-container {
  width: 80%;
  height: 100%;
  background-color: rgb(200, 200, 200);
  border-radius: 25px;
  display: flex;
  align-items: center;
  justify-content: center;
}
main {
  display: grid;
  justify-items: center;
  align-items: start;
}
form {
  margin-top: 150px;
  display: block;
  position: absolute;
  display: grid;
  width: 100%;
  height: fit-content;
  max-width: 420px;
  border: none;
  border-radius: 10px;
  background: whitesmoke;
  text-align: left;
  padding: 60px;
  z-index: 21;
}
label {
  color: #aaa;
  text-transform: uppercase;
  margin: 25px 0px 15px;
  display: inline-block;
  font-size: 0.9em;
}
input,
select {
  display: block;
  border: none;
  width: 100%;
  box-sizing: border-box;
  background-color: whitesmoke;
  border-bottom: 1px solid #e2bebe;
  padding: 5px 6px;
  margin-top: 10px;
  border-radius: 10px;
}
input:focus {
  outline: none;
  background-color: #e9e9e9;
}
select:focus {
  outline: none;
}
</style>
