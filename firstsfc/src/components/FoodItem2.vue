<template>
  <div class = "dango">
    <h2>{{ name }}</h2>
    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: 'The Dango',
      message: 'Squishy and different colors'
    }
  }
};
</script>

<style>
  .dango {
    border: dashed black 1px;
    display: inline-block;
    margin: 10px;
    padding: 10px;
    background-color: pink;
  }
  </style>