<script lang="ts">
	import { onMount } from 'svelte';
	import { Button } from '$lib/components/ui/button';
	import * as DropdownMenu from "$lib/components/ui/dropdown-menu";

	import AppWindow from 'lucide-svelte/icons/app-window';
	import HardDriveDownload from 'lucide-svelte/icons/hard-drive-download';
	import Monitor from 'lucide-svelte/icons/monitor';
	import Download from 'lucide-svelte/icons/download';
	import Github from 'lucide-svelte/icons/github';

	let os = '';

	function detectOS() {
		const userAgent = window.navigator.userAgent;

		if (userAgent.indexOf('Windows NT 10.0') !== -1) os = 'Windows';
		else if (userAgent.indexOf('Windows NT 6.2') !== -1) os = 'Windows';
		else if (userAgent.indexOf('Windows NT 6.1') !== -1) os = 'Windows';
		else if (userAgent.indexOf('Windows NT 6.0') !== -1) os = 'Windows';
		else if (userAgent.indexOf('Windows NT 5.1') !== -1) os = 'Windows';
		else if (userAgent.indexOf('Windows NT 5.0') !== -1) os = 'Windows';
		else if (userAgent.indexOf('Mac') !== -1) os = 'MacOS';
		else if (userAgent.indexOf('X11') !== -1) os = 'UNIX';
		else if (userAgent.indexOf('Linux') !== -1) os = 'Linux';
		else os = 'Unknown';
	}

	onMount(() => {
		detectOS();
	});
</script>

<style>
    .dl-height{
        min-height: 90vh;
    }
</style>

<div class="flex flex-col items-center justify-center dl-height">
	<h1 class="text-3xl font-bold mb-4">Download Spectre</h1>
	{#if os === 'Windows'}
		<div class="text-center p-4 pb-1">
			<DropdownMenu.Root>
				<DropdownMenu.Trigger>
					<Button size="lg" class="w-64">
						<Monitor class="mr-2 h-4 w-4" />
						Download for Windows
					</Button>
				</DropdownMenu.Trigger>
				<DropdownMenu.Content>
					<DropdownMenu.Group>
						<DropdownMenu.Label>
							Pick a Download
						</DropdownMenu.Label>
						<DropdownMenu.Separator />
						<DropdownMenu.Item>
							<AppWindow class="mr-2 h-4 w-4" />
							Portable EXE
						</DropdownMenu.Item>
						<DropdownMenu.Item>
							<HardDriveDownload class="mr-2 h-4 w-4" />
							MSI Installer
						</DropdownMenu.Item>
						<DropdownMenu.Item>
							<HardDriveDownload class="mr-2 h-4 w-4" />
							EXE Installer
						</DropdownMenu.Item>
					</DropdownMenu.Group>
				</DropdownMenu.Content>
			</DropdownMenu.Root>
		</div>
	{:else if os === 'MacOS'}
		<div class="text-center p-4 pb-1">
			<Button href="" size="lg" class="w-64">
				<Monitor class="mr-2 h-4 w-4" />
				Download for macOS
			</Button>
		</div>
		<div class="text-center p-4 pt-1 pb-1">
			<Button size="lg" class="w-64" variant="outline">
				<Download class="mr-2 h-4 w-4" />
				View All Downloads
			</Button>
		</div>
		<div class="text-center p-4 pt-1">
			<Button size="lg" class="w-64" variant="outline">
				<Github class="mr-2 h-4 w-4" />
				View Github Releases
			</Button>
		</div>
	{:else if os === 'Linux'}
		<div class="text-center">
			<p class="text-lg mb-4">We have detected that you are using Linux.</p>
			<Button href="/downloads/windows-installer.exe" size="lg" class="">
				Download for Linux
			</Button>
		</div>
	{:else}
		<div class="text-center">
			<p class="text-lg mb-4 text-muted-foreground">We couldn't detect your operating system.</p>
		</div>
	{/if}
	<div class="text-center p-4 pt-1 pb-1">
		<Button size="lg" class="w-64" variant="outline">
			<Download class="mr-2 h-4 w-4" />
			View All Downloads
		</Button>
	</div>
	<div class="text-center p-4 pt-1">
		<Button size="lg" class="w-64" variant="outline">
			<Github class="mr-2 h-4 w-4" />
			View Github Releases
		</Button>
	</div>
</div>
