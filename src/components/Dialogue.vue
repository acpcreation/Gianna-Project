<template>
  <div class="dialogue">
    <p>{{text}}</p>
  </div>
</template>

<script>
export default {
  name: 'DialogueComponent',
  props: {
    text: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .dialogue{
    /* width: 100%; */
    margin: 2vw;
    border-width: 8px;
    border-color: black;
    border-radius: 20px;
    border-style: solid;
    background-color: rgba(33, 33, 33, 0.9);
    padding: 20px;
    color:white;
    font-size: 24px;
    cursor: pointer;

    position: fixed;
    bottom: 0px;
    left: 2vw;
    right: 2vw;
  }
</style>
