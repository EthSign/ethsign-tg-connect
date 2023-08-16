

<template>
  <main class="main" ref="mainDomRef">

  </main>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue';
import { parseQuery } from 'vue-router';

const query = parseQuery(window.location.search);

const mainDomRef = ref<HTMLElement | null>(null);

(window as any).onTelegramAuth = function (user: any) {
  window.opener.postMessage({
    type: 'tg-brother:telegram_login',
    payload: user
  }, '*');

  if (query.close === '1') {
    setTimeout(() => {
      window.close();
    });
  }
}

onMounted(() => {
  const botName = query.bot_name as string || '';

  if (!botName) {
    document.write('bot_name is required');
  }

  const tgScriptEl = document.createElement('script');
  tgScriptEl.setAttributeNS(null, 'async', '');
  tgScriptEl.setAttribute('src', 'https://telegram.org/js/telegram-widget.js?22');
  tgScriptEl.setAttribute('data-telegram-login', botName);
  tgScriptEl.setAttribute('data-size', 'large');
  tgScriptEl.setAttribute('data-radius', '20');
  tgScriptEl.setAttribute('data-onauth', 'onTelegramAuth(user)');
  tgScriptEl.setAttribute('data-request-access', 'write');

  mainDomRef.value?.appendChild(tgScriptEl);
})

</script>

<style scoped>
.main {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>
