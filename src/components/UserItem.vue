<template>
  <div>
    <router-link :to="profileLink">{{user.name}} @{{user.username}}</router-link>
  </div>
</template>

<script>
export default {
  name: "UserItem",
  props: {
    user: {
      type: Object,
      required: true
    }
  },
  computed: {
    profileLink() {
      return `/user/${this.user.id}`;
    }
  }
};
</script>