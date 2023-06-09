<div id="translateLeft">
	<TopAppBar bind:this={topAppBar} variant="standard" dense>
		<Row>
			<Section>
			<Title>Thesis App</Title>
			</Section>
			<Section align="end">
				<Group variant="unelevated" style="display: flex; justify-content: stretch;">
					<Button href="/" color="secondary" variant="{$page.url.pathname ===  "/" ? "raised" : undefined}" ripple={false}>
						<Label>Home</Label>
					</Button>
					<Button href="history" color="secondary" variant="{$page.url.pathname ===  "/history" ? "raised" : undefined}" ripple={false}>
						<Label>History</Label>
					</Button>
				</Group>
			</Section>
		</Row>
	</TopAppBar>
</div>

<AutoAdjust {topAppBar}>
	<slot />
</AutoAdjust>
   
<script lang="ts">
	import { page } from '$app/stores';
	import TopAppBar, {
		Row,
		Section,
		Title,
		AutoAdjust,
	} from '@smui/top-app-bar';
	import Button, { Label, Group } from '@smui/button';

  	let topAppBar: TopAppBar;
</script>

<style>
	#translateLeft {
		transform: translate(-1px, -8px);
	}
	/* Hide everything above this component. */
	:global(#smui-app),
	:global(body),
	:global(html) {
		display: block !important;
		height: auto !important;
		width: auto !important;
		position: static !important;
	}

</style>