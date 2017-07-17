<template>
  <div id="app">
    <card class="card" v-for="project in projects" v-bind:project="project" v-bind:key="project.name" @clicked="onLike"></card>
  </div>
</template>

<script>
import firebase from 'firebase';
import Card from '@/components/Card';

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
