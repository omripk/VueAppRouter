<template>
  <div>
    <h1>{{userData.name}}</h1>
    <ul>
      <li>{{userData.phone}}</li>
      <li>{{userData.website}}</li>
      <li>{{userData.email}}</li>
    </ul>

    <router-link :to="postsLink">Posts</router-link>
  </div>
</template>

<script>
import UserItem from "./UserItem.vue";

export default {
  name: "UserProfile",
  data() {
    return {
      userData: {}
    };
  },
  computed: {
    postsLink() {
      return `/user/${this.$route.params.id}/posts`;
    }
  },
  created() {
      var id =this.$route.params.id;
      if(id){
    fetch(`https://jsonplaceholder.typicode.com/users/${id}`)
      .then(res => {
        return res.json();
      })
      .then(data => {
        this.userData = data;
      });
      }
  },
  components: { UserItem }
};
</script>
