<script>
  const options = [
    {
      id: "newIn",
      label: "New In",
      icon: "icons/new.png"
    },
    {
      id: "clothing",
      label: "Clothing",
      icon: "icons/clothes.png"
    },
    {
      id: "shoes",
      label: "Shoes",
      icon: "icons/shoes.png"
    },

    {
      id: "accessories",
      label: "Accessories",
      icon: "icons/woman.png"
    },
    {
      id: "activewear",
      label: "Activewear",
      icon: "icons/cycling.png"
    },
    {
      id: "giftsAndLiving",
      label: "Gifts & Living",
      icon: "icons/gift.png"
    },
    {
      id: "inspiration",
      label: "Inspiration",
      icon: "icons/diamond.png"
    }
  ];
</script>

<style type="text/scss">
  .sidebar-container {
    width: 20%;
    min-width: 220px;
    display: flex;
    flex-direction: column;
  }

  .store-icon-container {
    width: 100%;
    display: flex;
  }

  .store-icon-container img {
    max-width: 65%;
  }

  .explore-section {
    flex: 1;
    display: flex;
    flex-direction: column;
  }
  .explore-section-header {
    font-size: 26px;
    font-weight: bold;
    margin: 20px 0px;
  }

  .explore-options-container {
    flex: 1;
  }

  .explore-options {
    font-size: 14px;
    margin: 20px 0;
    cursor: pointer;
    display: flex;
  }

  .explore-options-img-container {
    display: flex;
    width: 40px;
  }

  .explore-options-img-container img {
    max-height: 25px;
    min-width: 25px;
  }

  .explore-options-label-container {
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>

<div class="sidebar-container">
  <div class="store-icon-container">
    <img src="images/my-store-app-icon.png" alt="app-logo" />
  </div>

  <div class="explore-section">
    <div class="explore-section-header">Explore</div>

    <div class="explore-options-container">
      {#each options as option}
        <div class="explore-options">
          <div class="explore-options-img-container">
            <img src={option.icon} alt={`explore-icon-${option.label}`} />
          </div>

          <div class="explore-options-label-container">{option.label}</div>
        </div>
      {/each}
    </div>
  </div>
</div>
