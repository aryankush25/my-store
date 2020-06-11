<script>
  import * as R from "ramda";
  import { unProtectedRoutes } from "../utils/helper.js";
  import { isTokensPresentLocalStorage } from "../services/utils/helper.js";
  import { goto } from "@sapper/app";

  export let segment;

  $: path = segment ? `/${segment}` : "/";

  const fetchAuthGuard = async route => {
    try {
      const isLoggedIn = isTokensPresentLocalStorage();
      const isProtectedRouted = !R.includes(route, unProtectedRoutes);

      if (isLoggedIn && !isProtectedRouted) {
        if (window) await goto("/");
      } else if (!isLoggedIn && isProtectedRouted) {
        if (window) await goto("/login");
      }
    } catch (error) {
      console.log("Error", error);
    }
  };

  $: fetchAuthGuard(path);

  $: showHeader = !R.includes(path, unProtectedRoutes);
</script>

<style type="text/scss">
  main {
    font-family: monospace;
  }
</style>

<main>
  <slot />
</main>
