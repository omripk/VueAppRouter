<template>
  <div>Hello User</div>
</template>

<script>
import UserItem from "./UserItem.vue";

export default {
  name: "UserProfile",
  data() {
    return {
      users: []
    };
  },
  created() {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then(res => {
        return res.json();
      })
      .then(users => {
        this.users = users;
      });
  },
  components: { UserItem }
};
</script>
