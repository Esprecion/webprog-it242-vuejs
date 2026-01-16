<template>
  <div class = "caviar">
    <h2>{{ name }}</h2>
    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: 'The Caviar',
      message: 'caviar is said to be a rich person food'
    }
  }
};
</script>

<style>
  .caviar {
    border: dashed black 1px;
    display: inline-block;
    margin: 10px;
    padding: 10px;
    background-color: #3E2723;
  }
  </style>