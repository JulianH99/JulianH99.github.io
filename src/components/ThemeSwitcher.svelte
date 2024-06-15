<script>
  let icons = {
    light: '/moon-icon.png',
    dark: '/sun-icon.png'
  }

  const darkMode = window.matchMedia("(prefers-color-scheme: dark)");

  let currentIcon = darkMode ? icons.dark : icons.light
  let currentTheme = darkMode ? 'dark' : 'light'

  function changeTheme() {
    if (currentIcon == icons.light) {
      currentIcon = icons.dark
      currentTheme = 'dark'
    } else {
      currentIcon = icons.light
      currentTheme = 'light'
    }
    window.dispatchEvent(new CustomEvent('theme:change', {detail: currentTheme}))
  }
</script>


<button class="header__theme-switcher" on:click={changeTheme}>
  <img src={currentIcon} alt="theme icon">
</button>
