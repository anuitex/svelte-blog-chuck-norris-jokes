<script>
	import { onMount } from 'svelte';
	import MainView from './MainView/index.svelte';
	import Tags from './Tags.svelte';
	import * as api from 'api.js';

	export let p = 1;

	let tab;
	let tag;
	let tags;

	function setTags({ detail }) {
		tag = detail.tag;
		tab = "tag";
	}
</script>

<svelte:head>
	<title>Blog</title>
</svelte:head>

<div class="home-page">
	<div class="">
		<div class="container">
			<h1 class="logo-font">Blog</h1>
		</div>
	</div>

	<div class="container page">
		<div class="row">
			<MainView {p} bind:tab />

		
		</div>
	</div>
</div>