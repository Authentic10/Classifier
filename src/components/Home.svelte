<script lang="ts">
    let cifarURL = 'https://www.cs.toronto.edu/~kriz/cifar.html'
</script>


<main>
    <h1 class="title is-2">CIFAR-10</h1>
    <p class="subtitle is-4">
        This web app is built to test a machine learning model built for the CIFAR-10 dataset on the cloud.
        The model is trained to predict ten (10) different classes : 
        <span>airplane, automobile, bird, cat, deer, dog, frog, horse, ship and truck.</span>
    </p>
    <p class="subtitle is-5">Click <a href="{cifarURL}" target="blank">here</a> for more information about the CIFAR-10 dataset.</p>
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