<template>
  <div>
    <h1>Hello Nette Camp 2019!</h1>

    <button @click.prevent="onLoad">Load users</button>

    <ul>
      <li v-for="user in users" :key="user.id">{{ user.name }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data: () => ({
    users: []
  }),
  methods: {
    async onLoad() {
      const res = await fetch("/api/users/");
      const data = await res.json();
      this.users = data;
    }
  }
};
</script>
