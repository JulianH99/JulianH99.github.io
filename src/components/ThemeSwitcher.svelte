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

<button class="header__theme-switcher" on:click={changeTheme} 
  aria-label="Change page theme">
  <img src={currentIcon} alt="Theme icon">
</button>

<style lang="scss">
  .header__theme-switcher {
    display: flex;
    align-items: center;
    justify-content: center;
    background: transparent;
    border: none;
    outline: none;
    width: 35px;
    height: 35px;
    transition: all .2s;
    padding: 2px;
    border-radius: 50%;
    cursor: pointer;

    img {
      max-width: 90%;
    }

    &:hover {
      background: var(--foreground);

      img {
        filter: invert(1);
      }
    }
  }
</style>
