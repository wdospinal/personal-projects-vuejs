<template>
  <div class="card">
    <img class="images" src="https://upload.wikimedia.org/wikipedia/commons/2/21/Flag_of_Colombia.svg" alt="Avatar" style="width:10%">
    <div class="container">
      <h2>
        <b>{{ project.name }} ({{ project.likes}})</b>
      </h2>
      <h3>
        <b>{{ project.url }}</b>
      </h3>
      <p>{{ project.content }}</p>
    </div>
    <div class="button">
      <button v-on:click="like(project)">LIKE</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'card',
  props: ['project'],
  methods: {
    like: function liekes(project) {
      this.$emit('clicked', project);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card {
  /* Add shadows to create the "card" effect */
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3s;
  font-family: Calibri, Trebuchet, sans-serif;
  background: #ED9B40;
  margin: 10px;
}

.images {
  margin: 10px;
}

.button {
  color: #ffffff
}


/* On mouse-over, add a deeper shadow */

.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
}



/* Add some padding inside the card container */

.container {
  padding: 2px 16px;
}
</style>
