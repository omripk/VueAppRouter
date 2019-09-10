<template>
  <div>
    <a @click="goBack" href="#">Go Back To User List</a>
    <h1>{{userData.name}}</h1>
    <ul>
      <li>{{userData.phone}}</li>
      <li>{{userData.website}}</li>
      <li>{{userData.email}}</li>
    </ul>

    <router-link :to="postsLink">Posts</router-link>
    <br />
    <router-link :to="nextUserLink">Next User Link</router-link>
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
  watch: {
    $route: "fetchData"
  },
  methods: {
    fetchData() {
      var id = this.$route.params.id;
      if (id) {
        fetch(`https://jsonplaceholder.typicode.com/users/${id}`)
          .then(res => {
            return res.json();
          })
          .then(data => {
            this.userData = data;
          });
      }
    },
    goBack() {
      this.$router.push({ name: "home" });

      // Yeni tabda -1 oldugu ıcın yenı sekmeye gıder
      //   this.$router.go("-1");
    }
  },
  computed: {
    postsLink() {
      return `/user/${this.$route.params.id}/posts`;
    },
    nextUserLink() {
      return `/user/${parseInt(this.$route.params.id) + 1}`;
    }
  },
  created() {
    this.fetchData();
  },
  components: { UserItem }
};
</script>
