<template>
  <div class="container">
    <h1>영화정보</h1>
    <div v-for="(movie) in data" :key="movie.id">
      <figure>
        <img :src="`${movie.imgUrl}`" :alt="movie.title" class="item" />
      </figure>
      <div class="info">
        <h3 class="bg-yellow" :style="textRed">{{ movie.title }}</h3>
        <p>개봉: {{ movie.year }}</p>
        <p>장르: {{ movie.category }}</p>
        <button @click="$emit('increaseLike', movie.id)">좋아요</button
        ><span>{{ movie.like }}</span>
        <p>
          <button @click="$emit('openModal', movie.id)">상세보기</button>
        </p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "MovieComponent",
  props: {
    data: Array,
  },
};
</script>
<style></style>
