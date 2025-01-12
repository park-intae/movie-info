<template>
  <div class="search-box">
    <input
      type="search"
      @change="
        $emit('searchMovie', inputText);
        inputText = $event.target.value;
        $event.target.value='';
        "
      placeholder="검색어 입력"
    />
    <button>검색</button>
  </div>
  <p>{{ inputText }}</p>
</template>
<script>
export default {
  name: "SearchbarComponent",
  data() {
    return {
      inputText: "",
    };
  },
  props: {
    data: Array,
  },
  watch: {
    inputText(name) {
      const findeName = this.data.filter((movie) => {
        movie.title.include(name);
      });
      if(findeName.length === 0) {
        alert("검색 결과가 없습니다.");
      }
    },
  },
};
</script>
<style>
.search-box {
  padding: 10px;
  display: flex;
  justify-content: center;
}

.search-box input {
  padding: 5px 10px;
}

.search-box button {
  margin: 0;
}
</style>
