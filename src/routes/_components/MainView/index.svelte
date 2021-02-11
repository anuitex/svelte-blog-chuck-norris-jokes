<script>
	import { stores } from '@sapper/app';
	import ArticleList from '../ArticleList/index.svelte';

	export let tab = 'all';
	export let p;

	const { session } = stores();

	function yourFeed() {
		tab = "feed";
	}

	function globalfeed() {
		tab = "all";
	}
</script>

<div class="col-md-9">
	<div class="feed-toggle">
		<ul class="nav nav-pills outline-active">
			{#if $session.user}
				<li class="nav-item">
					<a href="." class='nav-link {tab === "feed" ? "active" : "" }' on:click='{yourFeed}'>
						Your Feed
					</a>
				</li>
			{:else}
				<li class="nav-item">
					<a href="/login" class='nav-link'>
						Your Feed
					</a>
				</li>
			{/if}

			<li class="nav-item">
				<a href="." class='nav-link {tab === "all" ? "active" : "" }' on:click='{globalfeed}'>
					Global Feed
				</a>
			</li>
		</ul>
	</div>

	<ArticleList {p} {tab}/>
</div>