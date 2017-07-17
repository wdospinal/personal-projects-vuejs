<template>
  <div>
    <div class="modal-dialog" role="document">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">Add a project</h5>
          <button type="button" class="close" data-dismiss="modal" aria-label="Close">
            <span aria-hidden="true">&times;</span>
          </button>
        </div>
        <div class="modal-body">
          <div class="input-group entry">
            <span class="input-group-addon" id="basic-addon1">@</span>
            <input v-model="name" type="text" class="form-control" placeholder="Name" aria-describedby="basic-addon1">
          </div>
          <div class="input-group entry">
            <span class="input-group-addon" id="basic-addon3">https://</span>
            <input v-model="url" type="text" class="form-control" id="basic-url" aria-describedby="basic-addon3">
          </div>
          <div class="input-group entry">
            <span class="input-group-addon" id="basic-addon1">"</span>
            <input v-model="content" type="text" class="form-control" placeholder="Content" aria-describedby="basic-addon1">
          </div>  
          <div class="input-group entry">
            <span class="input-group-addon">#</span>
            <input v-model="likes" type="number" class="form-control" placeholder="Likes">
          </div>  
        </div>
        <div class="modal-footer">
          <button type="button" v-on:click="add()" class="btn btn-primary">Save</button>
          <button type="button" v-on:click="close()" class="btn btn-secondary" >Close</button>
        </div>
      </div>
    </div>
  </div>
</template>
<!-- template for the modal component -->

<script>
export default {
  name: 'add',
  methods: {
    add: function add() {
      const name = this.name || '';
      const url = this.url || '';
      const likes = this.likes || 0;
      const content = this.content || '';
      const project = { name, url, likes, content };
      this.$emit('added', project);
    },
    close: function close() {
      this.$emit('closed');
    },
  },
  data: function data() {
    return {
      showModal: false,
      name: '',
      url: '',
      likes: 0,
      content: '',
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.entry {
  margin: 8px
}
</style>
