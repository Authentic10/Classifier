<script lang="ts">

</script>

<main>
    <h1 class="title is-3">Please choose a file belonging one of the classes below</h1>
    <div class="columns">
        <div class="column">
          <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.pixelstalk.net%2Fwp-content%2Fuploads%2F2016%2F05%2FAirplane-HD-Wallpaper.jpg&f=1&nofb=1" alt="airplane" />
        </div>
        <div class="column">
          <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse3.mm.bing.net%2Fth%3Fid%3DOIP.XvScO1EgPiwghgX3Umh-CwHaE6%26pid%3DApi&f=1" alt="automobile">
        </div>
        <div class="column">
          <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse1.mm.bing.net%2Fth%3Fid%3DOIP.lr8bRv1cH7S7a995n3x9wAHaEK%26pid%3DApi&f=1" alt="bird">
        </div>
        <div class="column">
          <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse2.mm.bing.net%2Fth%3Fid%3DOIP.Sbtp6DnO5KP7WVNuygzhZwHaFH%26pid%3DApi&f=1" alt="cat">
        </div>
        <div class="column">
          <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse4.mm.bing.net%2Fth%3Fid%3DOIP.PIqYUtOfcCFEkHsadZjYngHaFa%26pid%3DApi&f=1" alt="deer">
        </div>
        <div class="column">
          <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse4.mm.bing.net%2Fth%3Fid%3DOIP.bBAdHie9rVifIiTHcTEr-gHaE8%26pid%3DApi&f=1" alt="dog">
        </div>
        <div class="column">
          <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse2.mm.bing.net%2Fth%3Fid%3DOIP.MO_7aWneKh8zsCIVaVgDlwHaGs%26pid%3DApi&f=1" alt="frog">
        </div>
        <div class="column">
          <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse1.mm.bing.net%2Fth%3Fid%3DOIP.vyrlywUhWj0aY1veG7ZHGAHaEK%26pid%3DApi&f=1" alt="horse">
        </div>
        <div class="column">
          <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse3.mm.bing.net%2Fth%3Fid%3DOIP.wISFZUucxoC43pP6QHlCowHaEo%26pid%3DApi&f=1" alt="ship">
        </div>
        <div class="column">
          <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse3.mm.bing.net%2Fth%3Fid%3DOIP.f7s_7WHfhHXlfJPZ64DnQAHaFj%26pid%3DApi&f=1" alt="truck">
        </div>
    </div>
    <div class="file is-centered is-boxed">
        <label class="file-label">
          <input class="file-input" type="file" accept="image/*" name="file">
          <span class="file-cta">
            <span class="file-icon">
              <i class="fa fa-upload"></i>
            </span>
            <span class="file-label">
              Choose a file…
            </span>
          </span>
        </label>
    </div>
    <div class="image is-centered">
      <img on:change="" src="" alt="user_pic" id="user_pic">
    </div>
</main>

<style lang="scss">
    main {
		text-align: center;
		padding: 1em;
		margin: 0 auto;
	}

  #user_pic {
    display: none;
  }
</style>