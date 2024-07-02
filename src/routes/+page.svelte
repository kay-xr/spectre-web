<!-- src/routes/Hero.svelte -->
<script lang="ts">
	import '$lib/styles/stars.css';
	import { Button } from '$lib/components/ui/button/index.js';
</script>

<style>
	.hero-height{
			min-height: 80vh;
	}
</style>



<main>
	<div class="stars-container">
		<div class="sky">
			<div class="stars"></div>
			<div class="stars1"></div>
			<div class="stars2"></div>
		</div>
	</div>

	<div class="flex flex-col items-center justify-center hero-height">
		<h1 class="text-4xl font-bold text-center">
			Simple and Lightweight Friends List Management for VRC
		</h1>
		<div class="mt-6 space-x-4">
			<Button size="lg" variant="outline" href="https://github.com/uhKayla/Spectre">
				Github
			</Button>
			<Button size="lg" href="https://github.com/uhKayla/Spectre/releases" >
				Download
			</Button>
		</div>
	</div>
</main>