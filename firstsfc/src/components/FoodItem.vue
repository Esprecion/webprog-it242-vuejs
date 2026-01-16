<template>
  <div class = "apples">
    <h2>{{ name }}</h2>
    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: 'The Apples',
      message: 'dont fall to far from the tree'
    }
  }
};
</script>

<style>
  .apples {
    border: dashed black 1px;
    display: inline-block;
    margin: 10px;
    padding: 10px;
    background-color: pink;
  }
  </style>