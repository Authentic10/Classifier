<script lang="ts">
    let datasetURL = 'https://www.kaggle.com/kritikseth/fruit-and-vegetable-image-recognition'
</script>


<main>
    <h1 class="title is-2">Fruits and Vegetables</h1>
    <p class="subtitle is-5">
        This web app is built to test a machine learning model built for a dataset trained on the cloud.
        The model is trained to predict different classes of fruits and vegetables: 
        <span>apple, banana, beetroot, carrot, corn, cucumber, ginger, lemon, lettuce, mango, onion, orange, potato, sweetpotato, tomato and watermelon.</span>
    </p>
    <p class="subtitle is-6">Click <a href="{datasetURL}" target="blank">here</a> for more information about the dataset.</p>
</main>


<style lang="scss" scoped>

	p {
		padding: 2em;
		max-width: 100%;
	}

	span {
		font-weight: bold;
	}

</style>
