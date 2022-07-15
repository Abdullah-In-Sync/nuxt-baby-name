<template>
  <div class="container">
    <h1>Baby Name Generator</h1>
    <p>Choose your options and click the "Find Names" buttom below</p>
    <div class="options-container">
      
      <Option v-for="option in optionsArray" :key="option.title" :option="option" :options="options" />
      <button class="primary" @click="computeNames">Find Name</button>


    </div>
    <div class="cards-container">
      <div class="card " v-for="name in selectedNames" :key="name">
        <div class="name-ct">
          <div>{{ name }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { Gender, Popularity, Length, names } from "@/data";
interface obj {
  gender: Gender;
  popularity: Popularity;
  length: Length;
}

const options = reactive<obj>({
  gender: Gender.BOY,
  popularity: Popularity.TRENDY,
  length: Length.ALL,
});

const selectedNames = ref<string[]>([]);

const computeNames = () => {
  const filterNames = names
    .filter((name) => name.gender === options.gender)
    .filter((name) => name.popularity === options.popularity)
    .filter((name) => {
      if (options.length === Length.ALL) return true;
      else return name.length === options.length;
    });
  selectedNames.value = filterNames.map((name) => name.name);
};

const optionsArray = [{
title: "1) Choose a gender",
category: "gender",
buttons: [ Gender.BOY, Gender.UNISEX, Gender.GIRL],
},{
title: "2) Choose a Popularity",
category: "popularity",
buttons: [ Popularity.TRENDY, Popularity.UNIQUE],
},{
title: "3) Choose a Name Length",
category: "length",
buttons: [ Length.SHORT, Length.ALL, Length.LONG],
}]
</script>

<style>
.name-ct {
  display: block;
}
.container {
  font-family: Arial, Helvetica, sans-serif;
  color: rgb(27, 60, 138);
  max-width: 50rem;
  margin: 0 auto;
  text-align: center;
}

h1 {
  font-size: 3rem;
}
.card {
  background-color: rgb(27, 60, 138);
  width: 28%;
  color: white;
  border-radius: 1rem;
  padding: 0.1rem;
  margin-right: 0.5rem;
  margin-bottom: 1rem;
  position: relative;
  height: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.card p {
  position: absolute;
  top: -29%;
  left: 92.5%;
  cursor: pointer;
  color: rgba(255, 255, 255, 0.178);
}

.options-container {
  background-color: rgb(255, 238, 236);
  border-radius: 2rem;
  padding: 1rem;
  width: 95%;
  margin: 0 auto;
  margin-top: 4rem;
  position: relative;
}

.primary {
  background-color: rgb(249, 87, 89);
  color: white;
  border-radius: 6.5rem;
  border: none;
  padding: 0.75rem 4rem;
  font-size: 1rem;
  margin-top: 1rem;
  cursor: pointer;
}

.cards-container {
  display: flex;
  margin-top: 3rem;
  flex-wrap: wrap;
}

.option-container {
  margin-bottom: 2rem;
}

.option {
  background: white;
  outline: 0.15rem solid rgb(249, 87, 89);
  border: none;
  padding: 0.75rem;
  width: 12rem;
  font-size: 1rem;
  color: rgb(27, 60, 138);
  cursor: pointer;
  font-weight: 200;
}

.option-left {
  border-radius: 0;
}

.option-right {
  border-radius: 0;
}

.option-active {
  background-color: rgb(249, 87, 89);
  color: white;
}
</style>
