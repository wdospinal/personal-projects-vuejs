<template>
  <div id="app">
    <card class="card" v-for="project in projects" v-bind:project="project" v-bind:key="project.name" @clicked="onLike"></card>
    <button id="show-modal" @click="showModal = !showModal">Show Modal</button>
    <add v-if="showModal"  @added="onAdd" @closed="showModal = false"></add>
  </div>
</template>

<script>
import firebase from 'firebase';
import Card from '@/components/Card';
import Add from '@/components/Add';

const config = {
  apiKey: 'AIzaSyCT_JcNuLP0N947hKlbI56lVznRKggxxkI',
  authDomain: 'personalprojectsshared.firebaseapp.com',
  databaseURL: 'https://personalprojectsshared.firebaseio.com',
  projectId: 'personalprojectsshared',
  storageBucket: 'personalprojectsshared.appspot.com',
  messagingSenderId: '31449931878',
};
const app = firebase.initializeApp(config);
const db = app.database();

const projectsRef = db.ref('messages');

export default {
  name: 'app',
  components: {
    Card,
    Add,
  },
  data: function data() {
    return {
      showModal: false,
    };
  },
  methods: {
    onLike(value) {
      const name = value.name || '';
      const url = value.url || '';
      const likes = value.likes || 0;
      const content = value.content || '';
      const saveValue = { name, url, likes, content };
      const key = value['.key'];
      saveValue.likes += 1;
      const updates = {};
      updates[`/messages/${key}`] = saveValue;
      return db.ref().update(updates);
    },
    onAdd(project) {
      this.showModal = false;
      return projectsRef.push(project);
    },
  },
  firebase: {
    projects: projectsRef,
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
