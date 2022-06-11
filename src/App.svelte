<script>
  import { fade } from 'svelte/transition';
  import css from './lib/style.css';
  import Switch from './lib/Switch.svelte';
  import { t, locale, locales } from "./lib/i18n";

  let dark = false;
  
  $: theme = dark ? 'dark' : 'lite';

  let count = 0;
  let delay = 1;
  
  delay = delay * 1000;
  const increment = () => {
    if (count >= 100) return;
    count += 1;
  }
  
  let random = `${Math.floor(Math.random() * 9) + 1} * ${Math.floor(Math.random() * 9) + 1}`;
  let res = eval(random);

  let userBrowserLang = navigator.language;
  if (userBrowserLang.includes('-')) userBrowserLang = userBrowserLang.split('-')[0];

  if (!locales.includes(userBrowserLang)) userBrowserLang = 'en';

  $locale = userBrowserLang;
</script>

<main>
  <Switch bind:checked={ dark } key="bg"></Switch>

  {#if count == res}
    <h1 in:fade="{{ duration: delay }}" class={ theme }>{ $t("done") }</h1>
    <h2 in:fade="{{ delay: delay, duration: delay }}" class={ theme }>{ $t("sub") }</h2>
    <button in:fade="{{ delay: delay * 2, duration: delay * 0.5 }}" class={ theme }>{ $t("move") }</button>
  {:else}
    <h1 class={ theme }>{ $t("request") }<br>{ random }</h1>
    <p class={ theme }>{ count }</p>
    <input type=range bind:value={ count } min="0" max="100" class={ theme }>
    <button on:click={increment} class={ theme }>{ $t("cl") }</button>
  {/if}
</main>