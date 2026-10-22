<template>
  <div class="page center">
    <h2>Вход</h2>
    <form @submit.prevent="login">
      <input v-model="password" type="password" placeholder="Пароль (введите 'demo')" />
      <button type="submit">Войти</button>
    </form>
    <p v-if="error" style="color: red; margin-top: 0.5rem">
      {{ error }}
    </p>
  </div>
  <RouterLink to="/" class="btn-back">← На главную</RouterLink>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";

const password = ref("");
const error = ref(null);
const router = useRouter();

const login = () => {
  error.value = null;
  if (password.value === "demo") {
    localStorage.setItem("token", "demo");
    router.push({ name: "Dashboard" });
  } else {
    error.value = 'Неверный пароль. Попробуйте "demo"';
  }
};
</script>

<style scoped>
.center {
  text-align: center;
}
input {
  padding: 0.5rem;
  margin-right: 0.5rem;
}
button {
  padding: 0.5rem 1rem;
}
.btn-back {
  width: 200px;
  display: inline-block;
  margin-bottom: 1rem;
  padding: 0.5rem 1rem;
  text-decoration: none;
  background: #eee;
  color: #333;
  border-radius: 4px;
}
.btn-back:hover {
  background: #ddd;
}
</style>
