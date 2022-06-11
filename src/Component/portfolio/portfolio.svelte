<script>
    import { fade } from 'svelte/transition';
    import css from '../../lib/style.css';
    import Switch from '../../lib/Switch.svelte';
    import { t, locale, locales } from "../../lib/i18n";
  
    let dark = false;
    
    $: theme = dark ? 'dark' : 'lite';
    let delay = 1;
    
    delay = delay * 1000;
  
    let userBrowserLang = navigator.language;
    if (userBrowserLang.includes('-')) userBrowserLang = userBrowserLang.split('-')[0];
  
    if (!locales.includes(userBrowserLang)) userBrowserLang = 'en';
  
    $locale = userBrowserLang;
</script>
  
<Switch bind:checked={ dark } key="bg"></Switch>
<h1 in:fade="{{ duration: delay }}" class={ theme }>Hello World</h1>