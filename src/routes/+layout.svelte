<script>
	import '../app.css';
	import { ModeWatcher } from "mode-watcher";
	import Header from '$lib/components/Header.svelte';
</script>

<Header />
<ModeWatcher />
<slot></slot>
