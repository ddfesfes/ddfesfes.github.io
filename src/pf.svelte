<script>
    import { fade } from 'svelte/transition';
    import css from './lib/style.css';
    import { t, locale, locales } from "./lib/i18n";
    import dark from './App.svelte';
    alert(dark);

    $: theme = dark ? 'dark' : 'lite';
    let delay = 1;
    
    delay = delay * 1000;
  
    let userBrowserLang = navigator.language;
    if (userBrowserLang.includes('-')) userBrowserLang = userBrowserLang.split('-')[0];
  
    if (!locales.includes(userBrowserLang)) userBrowserLang = 'en';
  
    $locale = userBrowserLang;
</script>

<h1 in:fade="{{ duration: delay }}" class={ theme }>{ $t("done") }</h1>
<h2 in:fade="{{ delay: delay, duration: delay }}" class={ theme }>{ $t("sub") }</h2>
<button in:fade="{{ delay: delay * 2, duration: delay * 0.5 }}" class={ theme }>{ $t("move") }</button>