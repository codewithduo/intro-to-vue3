<script setup>
import { ref, computed } from "vue";
import { RouterLink } from "vue-router";
import hitLogo from "@/assets/hit-logo.jpeg";

const clubName = ref("HIT");
const clubGenerationNumber = ref(13);

const clubTitle = computed(() => {
  return `${clubName.value} ${clubGenerationNumber.value}`;
});

const navigationLinks = [
  {
    id: 1,
    name: "Home",
    path: "/",
  },
  {
    id: 2,
    name: "About",
    path: "about",
  },
  {
    id: 3,
    name: "Blog",
    path: "blog",
  },
  {
    id: 4,
    name: "Contact",
    path: "contact",
  },
  {
    id: 4,
    name: "Courses",
    path: "courses",
  },
  {
    id: 4,
    name: "OLP",
    path: "olp",
  },
];
</script>
<template>
  <div class="default-layout">
    <header class="header">
      <div class="brand">
        <img class="logo" :src="hitLogo" alt="HIT CLUB LOGO" />
        <h1 class="title">{{ clubTitle }}</h1>
      </div>
      <div class="navigation-bar">
        <RouterLink
          class="link"
          v-for="link in navigationLinks"
          :href="link.path"
          :to="link.path"
          >{{ link.name }}</RouterLink
        >
      </div>
      <div v-if="isLoggedIn" class="user-info">
        <div class="avatar"></div>
        <h3 class="name">{{ userLoggedIn }}</h3>
      </div>
      <div v-else class="user-actions">
        <button type="button" class="login">
          <RouterLink to="login">Login</RouterLink>
        </button>
      </div>
    </header>
    <main class="main-content">
      <slot />
    </main>
  </div>
</template>
<style scoped>
.default-layout > .header {
  padding: 0 32px;
  border-bottom: 1px solid orange;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 32px;
}

.default-layout > .header > .brand {
  display: flex;
  align-items: center;
}

.default-layout > .header > .brand > .title {
  font-weight: 600;
  margin-left: 8px;
  color: orange;
}

.default-layout > .header > .brand > .logo {
  width: 50px;
  height: 50px;
}

.default-layout > .header > .navigation-bar {
  flex-grow: 1;
  display: flex;
  gap: 48px;
  justify-content: center;
}

.default-layout > .header > .navigation-bar > .link {
  color: #333;
  text-decoration: none;
  font-size: 20px;
  font-weight: 600;
}

.default-layout > .header > .user-info {
  width: 15%;
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
  justify-content: flex-end;
}

.default-layout > .header > .user-info > .avatar {
  height: 50px;
  width: 50px;
  background-color: orange;
  border-radius: 50%;
}

.default-layout > .header > .user-actions {
  width: 15%;
  display: flex;
  align-items: center;
  justify-content: end;
  gap: 8px;
}

.default-layout > .header > .user-actions > .login {
  padding: 8px 16px;
  cursor: pointer;
  background-color: orange;
  outline: none;
  border: none;
  transition: ease-in 0.5s;
  border-radius: 8px;
}

.default-layout > .header > .user-actions > .login:hover {
  background-color: rgb(247, 198, 106);
}

.default-layout > .main-content {
  padding: 32px;
}
</style>
