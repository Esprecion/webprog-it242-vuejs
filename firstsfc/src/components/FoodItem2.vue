<template>
  <div class = "Dango" >
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
  .Dango {
    border: dashed black 1px;
    display: inline-block;
    margin: 10px;
    padding: 10px;
    background-color: lightgreen;
  }
  </style>