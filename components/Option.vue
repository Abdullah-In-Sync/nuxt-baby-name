<template>
    <div class="option-container">
        <h4>{{option.title}}</h4>
        <div class="option-buttons">
            <button v-for="value in option.buttons" @click="options[option.category] = value " class="option option-left"
                :class="options[option.category] === value && 'option-active'">{{value}}</button>
            <!-- <button @click="options.gender = Gender.UNISEX" class="option"
                :class="options.gender === Gender.UNISEX && 'option-active'">Unisex</button>
            <button @click="options.gender = Gender.GIRL" class="option option-right"
                :class="options.gender === Gender.GIRL && 'option-active'">Girl</button>
        </div>
    </div>
    <div class="option-container">
        <h4>2) Choose a Popularity</h4>
        <div class="option-buttons">
            <button @click="options.popularity = Popularity.UNIQUE" class="option option-left"
                :class="options.popularity === Popularity.UNIQUE && 'option-active'">Unique</button>
            <button @click="options.popularity = Popularity.TRENDY" class="option option-right"
                :class="options.popularity === Popularity.TRENDY && 'option-active'">Trendy</button>
        </div>
    </div>
    <div class="option-container">
        <h4>3) Choose a Name Length</h4>
        <div class="option-buttons">
            <button @click="options.length = Length.SHORT" class="option option-left"
                :class="options.length === Length.SHORT && 'option-active'">Short</button>
            <button @click="options.length = Length.ALL" class="option option"
                :class="options.length === Length.ALL && 'option-active'">All</button>
            <button @click="options.length = Length.LONG" class="option option-right"
                :class="options.length === Length.LONG && 'option-active'">Long</button>
                -->
        </div> 
    </div>
</template>
<script setup lang="ts">
import { Gender, Length, Popularity } from "@/data";

interface OptionProps {
    option: {
        title: string;
        category: string;
        buttons: Gender[] | Popularity[] | Length[];
    };
    options: {
        gender: Gender;
        popularity: Popularity;
        length: Length;
    };
}

const props = defineProps<OptionProps>();
</script>