<script >

  let showMore = false;
  let fileName = 'No file uploaded';
  let fileURL = '';
  let isThereAFile = false;
  let predButton = true;
  let prediction;

  function showMoreToggle(){
    showMore = !showMore;
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

function changeFile(){
    let userFile = document.getElementById('change-file');
    let predClasses = document.getElementById('pred-classes');
    
    predClasses.style.display = 'none';
    let reader = new FileReader();
    if('files' in userFile){
      //alert(userFile.files.length);
      if (userFile.files.length > 0) {

        let fileSize = userFile.files[0].size;

        if(fileSize > 4000000){
          alert('File size can\'t be greater than 4 MB');
        } else {
          fileName = userFile.files[0].name;
          //isThereAFile = !isThereAFile;
          predButton = !predButton;
          reader.onload = () => {
            fileURL = reader.result;
          }
        reader.readAsDataURL(userFile.files[0]);
        }
    }
  }
    
}

async function getPrediction(){
  const blob = await (await fetch(fileURL)).blob();
  const response = await fetch('https://fruits-and-vegetables.cognitiveservices.azure.com/customvision/v3.0/Prediction/98fcb0c4-6c97-4607-bf60-773b6f97359f/classify/iterations/Iteration1/image', {
    method: "POST",
    body: blob,
    headers: {
              "Prediction-Key": "6d29ca369cf849de8821ed35cb1f0867",
              "Content-Type": "application/octet-stream"
            }
  });

  let predict = await response.json();

  if(response.ok){
    predButton = !predButton;
    let predClasses = document.getElementById('pred-classes');  
    if(predClasses != null) {
      predClasses.style.display = 'block';
    }
    return predict
  } else {
    throw new Error(predict)
  }

}


function submitHandler(e){
  prediction = getPrediction();
}

</script>

<main>
    <h1 class="title is-3">Please, choose an image</h1>
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
        </ul>
      </div>
      {#if !isThereAFile}
      <div class="file is-centered is-boxed is-primary has-name">
        <label class="file-label">
          <input id="user-file" class="file-input" type="file" name="user-file" accept="image/*" on:change="{displayFile}">
          <span class="file-cta">
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
        {#if predButton}
        <div class="field mt-2">
          <div class="control">
            <button class="button is-primary" on:click|preventDefault="{submitHandler}">Predict</button>
          </div>
        </div>
        {:else}
        <div class="file is-centered is-boxed is-primary has-name mb-2">
          <label class="file-label">
            <input id="change-file" class="file-input" type="file" name="user-file" accept=".jpg, .png, .jpeg" on:change="{changeFile}">
            <span class="file-cta">
              <span class="file-label">
                Change file
              </span>
            </span>
            <span class="file-name">
              {fileName}
            </span>
          </label>
        </div>
        {/if}
      {/if}
      {#if prediction === undefined}
        <p></p>
      {:else}
      {#await prediction} 
        <p>Loading ...</p>
      {:then value } 
      <p class="subtitle is-6">
        <span class="has-text-weight-bold">Prediction :</span> {value.predictions[0].tagName} - <span class="has-text-weight-bold">Score :</span> {value.predictions[0].probability}
      </p>
      <button class="button is-small" on:click="{showMoreToggle}">Scores for all</button>
      {#if showMore}
      <div id="pred-classes" >
        {#each value.predictions as pred}
          <p>{pred.tagName} : {pred.probability}</p> 
        {/each}
      </div>
      {/if}
      {:catch error}
      {error.message}
      {/await}
      {/if}
    </div> 
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