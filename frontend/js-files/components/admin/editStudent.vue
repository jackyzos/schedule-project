<template>
  <div class="hero">
    <div v-if="user.id != $route.params.userId" class="notification is-danger">
      this user are not found
    </div>
<div class="" v-else="" >
    <p>{{msg}} : {{ $route.params.userId }}</p>
    <p class="notification is-info" v-if="msgEdit.length > 0">{{msgEdit}}</p>
    <p class="control">
      <label class="label" for="username">Student Name</label>
      <input v-model="user.name" class="input" type="text" id="username" placeholder="student Name">
  </p>
    <p class="control">
      <label class="label" for="fullName">Course ID</label>
      <input v-model="user.courseid" class="input" type="text" id="fullName" placeholder="student Course">
      </p>
      <button class="button" @click.prevent="letsEdit()">Save</button>
      <button class="button" @click="$router.go(-1)">Cancel</button>
    </div>

</div>

  </div>
</template>
<script>
export default {
  name: 'AddNewStudent',
  data(){
    return{
      user: {
        name:null,
        courseid: null
      },
   msg:'Current Student Id',
   msgEdit: ''
    }
  },
  computed: {

 },
  methods: {
    letsEdit(){
      let den = this
      let id = den.$route.params.userId
      fetch('http://localhost:3000/admin/getStudents/'+ id, {
        body: JSON.stringify({ name: den.user.name, courseid: den.user.courseid }),
        headers: {
          'Content-Type': 'application/json'
        },
        method: 'PUT'
      })
  .then(function (response) {
    return response.json()
  })
  .then(function (result) {
    den.msgEdit = 'Student was updated'
    setTimeout(function(){
      den.$router.go(-1)
   }, 3000)
    console.log(result)
  })
         // return this.$store.getters['getSingleStudent'](this.$route.params);
      // this.$store.dispatch('patchPerson', this.person);
    //   this.$store.commit('EDIT_STUDENT', this.user).then(() => {
    //   // this.$socket.emit('editItem', {
    //   //   name: this.itemName,
    //   //   prevName: this.currentlyEditingName
    //   //             });
    //   console.log('teststse');
    // })
    }
},
 mounted() {
        let id = this.$route.params.userId
        return this.user = this.$store.getters.loadAll.find((p) => p.id === id) || {}
        // this.user = this.$store.getters.getItem
    },
}
// </script>
<style lang="css" scoped>
button{
  margin-top: 25px;
}
</style>
