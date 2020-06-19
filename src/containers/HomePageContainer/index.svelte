<style type="text/scss">
  .home-page-container {
    background-color: #bde7f0;
    height: 100vh;
    width: 100vw;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 15px;
    box-sizing: border-box;
  }

  .home-page-wrapper {
    background-color: #ffffff;
    height: 100%;
    width: 100%;
    border-radius: 30px;
    box-sizing: border-box;
    padding: 30px 0;
  }

  .home-page-inner-wrapper {
    height: 100%;
    width: 100%;
    overflow: auto;
    padding: 0 30px;
    box-sizing: border-box;
  }
</style>

<div class="home-page-container">
  <div class="home-page-wrapper">
    <div class="home-page-inner-wrapper">
      <slot />
    </div>
  </div>
</div>
