<script >

  let imageTab = true;
  let fileName = 'No file uploaded';
  let fileURL = '';
  let isThereAFile = false;

  function tabToggle(){
    imageTab = !imageTab;
  }


  function displayFile(){
    let userFile = document.getElementById('user-file');
    let reader = new FileReader();
    if('files' in userFile){
      //alert(userFile.files.length);
      if (userFile.files.length > 0) {

        let fileSize = userFile.files[0].size;

        if(fileSize > 4000000){
          alert('File size can\'t be greater than 4 MB');
        } else {
          fileName = userFile.files[0].name;
          isThereAFile = !isThereAFile;
          reader.onload = () => {
            fileURL = reader.result;
          }
        reader.readAsDataURL(userFile.files[0]);
        }
    }
  }
    
}

</script>

<main>
    <h1 class="title is-3">Please, choose an image or paste a link</h1>
    {#if imageTab}
    <div >
      <div class="tabs is-centered is-toggle">
        <ul>
          <li class="is-active">
            <!-- svelte-ignore a11y-missing-attribute -->
            <a>
              <span class="icon is-small">
                <i class="fa fa-image" aria-hidden="true"></i>
              </span>
              <span>Image</span>
            </a>
          </li>
          <!-- svelte-ignore a11y-missing-attribute -->
          <li>
            <a on:click="{tabToggle}">
              <span class="icon is-small">
                <i class="fa fa-link" aria-hidden="true"></i>
              </span>
              <span>Link</span>
            </a>
          </li>
        </ul>
      </div>
      {#if !isThereAFile}
      <div class="file is-centered is-boxed is-primary has-name">
        <label class="file-label">
          <input id="user-file" class="file-input" type="file" name="user-file" accept=".jpg, .png, .jpeg" on:change="{displayFile}">
          <span class="file-cta">
            <!--<span class="file-icon ml-6">
              <i class="fa fa-upload"></i>
            </span>-->
            <span class="file-label">
              Choose a file…
            </span>
          </span>
          <span class="file-name">
            {fileName}
          </span>
        </label>
      </div>
      {/if}
      {#if isThereAFile}
      <div class="img">
        <img src="{fileURL}" alt="File to predict">
      </div>
      <div class="field mt-2">
        <div class="control">
          <button class="button is-primary">Predict</button>
        </div>
      </div>
      {/if}
    </div>
    {/if}

    {#if !imageTab}
    <div class="link">
      <div class="tabs is-centered is-toggle">
        <ul>
          <li>
            <!-- svelte-ignore a11y-missing-attribute -->
            <a on:click="{tabToggle}">
              <span class="icon is-small">
                <i class="fa fa-image" aria-hidden="true"></i>
              </span>
              <span>Image</span>
            </a>
          </li>
          <!-- svelte-ignore a11y-missing-attribute -->
          <li class="is-active">
            <a>
              <span class="icon is-small">
                <i class="fa fa-link" aria-hidden="true"></i>
              </span>
              <span>Link</span>
            </a>
          </li>
        </ul>
      </div>
      <div class="field">
        <p class="control has-icons-left">
          <input class="input" type="text" placeholder="Link">
          <span class="icon is-small is-left">
            <i class="fa fa-link"></i>
          </span>
        </p>
        <div class="field">
          <div class="control">
            <button class="button is-primary">Submit</button>
          </div>
        </div>
      </div>
    </div>  
    {/if}
</main>

<style lang="scss">
    main {
		text-align: center;
		padding: 1em;
		margin: 0 auto;
    width: 80%;
	}

  img {
    max-width: auto;
    max-height: auto;
  }
 
</style>