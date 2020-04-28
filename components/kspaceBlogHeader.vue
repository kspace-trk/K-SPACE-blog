<template>
  <div class="header-wrapper">
    <nuxt-link to="/" tag="div" class="steg-logo">
      <img src="~/assets/img/kspace-header-logo.png" alt="Steg Logo" />
    </nuxt-link>
    <div class="header-sub-icon">
      <a href="https://soundcloud.com/k-space_1" target="_blank">
        <img src="~/assets/img/SoundCloud-icon.png" alt="SoundCloud icon" />
      </a>
      <a href="https://www.instagram.com/kspace_trk/" target="_blank">
        <img src="~/assets/img/instagram-white-icon.png" alt="Instagram icon" />
      </a>
      <a href="https://twitter.com/Kspace_trk" target="_blank">
        <img src="~/assets/img/twitter-icon.png" alt="Twitter icon" />
      </a>
    </div>
  </div>
</template>

<style>
.header-wrapper {
  height: 70px;
  width: 100%;
  background-color: #404040;
  display: flex;
  align-items: center;
  justify-content: space-between;
  line-height: 1;
}
.steg-logo {
  margin: auto auto auto 30px;
  cursor: pointer;
}
.steg-logo img {
  height: 55px;
}
.header-sub-icon {
  margin-right: 40px;
}

.header-sub-icon img {
  width: 30px;
  margin-left: 50px;
}
/*----------424px以下------------*/
@media screen and (max-width: 424px) {
  .steg-logo {
    margin: auto auto auto 12px;
    cursor: pointer;
  }
  .header-sub-icon {
    margin-right: 15px;
  }

  .header-sub-icon img {
    width: 25px;
    height: 25px;
    margin-left: 30px;
  }
}
/*----------324px以下------------*/
@media screen and (max-width: 324px) {
  .header-sub-icon {
    margin-right: 15px;
  }

  .header-sub-icon img {
    width: 25px;
    height: 25px;
    margin-left: 20px;
  }
}
</style>