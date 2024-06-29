<template>
  <div class="movie-wrapper grid medium-space large-padding">
    <div v-for="(item, i) in state" :key="i" class="s4">
      <img :src="item.image" alt="movie poster" class="image-container" />
      <div class="item-content">
        <h5>{{ item.name }}</h5>
        <nav class="wrap no-margin">
          <div v-for="(genre, j) in item.genres" :key="j">
            <div class="badge indigo7 none no-margin">{{ genre }}</div>
          </div>
        </nav>
        <p>{{ item.description }}</p>
        <nav class="bottom-padding">
          <p>Rating: ({{ item.rating }}/5)</p>
          <div class="icon-container">
            <StarIcon
              v-for="star in item.rating"
              :key="star"
              class="icon-rating"
            />
          </div>
        </nav>
      </div>
    </div>
  </div>
</template>
<script setup>
import { reactive } from "vue";
import { items } from "./movies.json";
import { StarIcon } from "@heroicons/vue/24/solid";

const state = reactive(items);
</script>
<style lang="scss" scoped>
.movie-wrapper {
  .item-content {
    background-color: rgb(240, 236, 245);
    border-radius: 0.5rem;
    padding: 0.5rem;
    height: 300px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;

    & > :last-child {
      margin-top: auto;
    }
  }
  .image-container {
    width: 100%;
    height: 600px;
  }
  .icon-container {
    display: flex;
    flex-wrap: nowrap;
    .icon-rating {
      width: 20px;
      height: 20px;
      color: gold;
    }
  }
}
</style>
