<script>
  import HomePageContainer from "../containers/HomePageContainer/index.svelte";
  import SideBar from "../components/SideBar/index.svelte";
  import HomePageContent from "../components/HomePageContent/index.svelte";
</script>

<style type="text/scss">
  .home-page-content-container {
    height: 100%;
    width: 100%;
    display: flex;
  }
</style>

<svelte:head>
  <title>My Store</title>
</svelte:head>

<HomePageContainer>
  <div class="home-page-content-container">
    <SideBar />
    <HomePageContent />
  </div>
</HomePageContainer>
