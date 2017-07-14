<template>
  <div class='projects'>
    <h1>List Projects</h1>
    <card class ="card" v-for="project in projects" v-bind:project="project" v-bind:key="project.name" @clicked="onLike"></card>
  </div>
</template>

<script>
import Card from '@/components/Card';

export default {
  name: 'projects',
  components: {
    Card,
  },
  methods: {
    onLike(value) {
      console.log(value); // someValue
    },
  },
  data() {
    return {
      projects: [{
        name: 'Colombia',
        url: 'colombia.co',
        likes: 5,
        content: 'Colombia, oficialmente República de Colombia, es un país soberano situado en la región noroccidental de América del Sur. Está constituido en un estado unitario, social y democrático de derecho cuya forma de gobierno es presidencialista.',
      },
      {
        name: 'Colombia',
        url: 'colombia.co',
        likes: 5,
        content: 'Colombia, oficialmente República de Colombia, es un país soberano situado en la región noroccidental de América del Sur. Está constituido en un estado unitario, social y democrático de derecho cuya forma de gobierno es presidencialista.',
      }],
    };
  },
};
</script>

<!-- Add 'scoped' attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
.card {
  margin: 8px;
}
</style>
