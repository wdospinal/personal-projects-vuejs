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
      <button class="btn orange"  v-on:click="like(project)">LIKE</button>
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

.btn {
  position: relative;

  font-size: 150%;
  display: block;
  margin: 30px auto;
  padding: 0;
  
  height: 50px;
  width: 25%;

  overflow: hidden;

  border-width: 0;
  outline: none;
  border-radius: 2px;
  box-shadow: 0 1px 4px rgba(0, 0, 0, .6);
  
  background-color: #2ecc71;
  color: #ecf0f1;
  
  transition: background-color .3s;
}

.btn:hover, .btn:focus {
  background-color: #27ae60;
}

.btn > * {
  position: relative;
}

.btn span {
  display: block;
  padding: 12px 24px;
}

.btn:before {
  content: "";
  
  position: absolute;
  top: 50%;
  left: 50%;
  
  display: block;
  width: 0;
  padding-top: 0;
    
  border-radius: 100%;
  
  background-color: rgba(236, 240, 241, .3);
  
  -webkit-transform: translate(-50%, -50%);
  -moz-transform: translate(-50%, -50%);
  -ms-transform: translate(-50%, -50%);
  -o-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
}

.btn:active:before {
  width: 120%;
  padding-top: 120%;
  
  transition: width .2s ease-out, padding-top .2s ease-out;
}

.btn.orange {
  background-color: #e67e22;
}

.btn.orange:hover, .btn.orange:focus {
  background-color: #d35400;
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
