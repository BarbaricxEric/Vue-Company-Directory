<script setup>
  import { ref } from 'vue'
  import { useAuth } from '@/composables/useAuth'

  const { isAuthenticated, logout, user } = useAuth()
  const brand = ref(import.meta.env.VITE_APP_NAME)
</script>

<template>
  <nav>
    <div class="wrapper">
      <RouterLink :to="{ name: 'Home' }" class="brand">
        <span class="brand-title">{{ brand }}</span>
      </RouterLink>
      <div class="menu">
        <div v-if="isAuthenticated">
          <p v-show="isAuthenticated" class="px-11 py-1">
            Welcome back
            <strong
              ><i>{{ user.name }}</i></strong
            >
          </p>
          <RouterLink :to="{ name: 'Home' }" href="#" class="menu-item">Departments</RouterLink>
          <RouterLink :to="{ name: 'Settings' }" href="#" class="menu-item">Settings</RouterLink>
          <button href="#" class="menu-logout" @click="logout">Logout</button>
        </div>
        <div v-else>
          <RouterLink :to="{ name: 'Login' }" href="#" class="menu-login">Login</RouterLink>
        </div>
      </div>
    </div>
  </nav>
</template>

<style scoped lang="postcss">
  nav {
    @apply flex h-20 bg-gray-600 text-slate-200;
    .wrapper {
      @apply container mx-auto flex w-full items-center justify-between;

      .brand {
        &-title {
          @apply text-2xl font-bold text-blue-500;
        }
      }
      .menu {
        @apply flex gap-2;
        div {
          @apply py-2;
        }
        &-item {
          @apply rounded-md px-4 py-2 hover:bg-blue-500 hover:text-white;
        }
        &-login {
          @apply rounded-md bg-green-400 px-4 py-2 text-red-100 hover:bg-green-800;
        }
        &-logout {
          @apply mx-2 rounded-md bg-red-400 px-4 py-2 text-red-100 hover:bg-red-800;
        }
      }
    }
  }
</style>