
<script lang="ts">
	import './styles/main.scss';
	import {Router, Route} from 'svelte-routing';
	import Header from './components/Header.svelte';
	import Home from './components/Home.svelte';
	import Footer from './components/Footer.svelte';
	import Azure from './components/Azure.svelte';

	export let url = "";
</script>

<Router {url}>
	<Header/>
	<main>
		<Route path='azure' component={Azure} />
		<Route path='/'><Home/></Route>
	</main>
</Router>
<Footer/>

<style lang="scss">
	main {
		text-align: center;
		padding: 4em;
		margin: 0 auto;
	}

</style>