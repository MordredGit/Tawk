<script lang="ts">
	import logo from '$lib/assets/images/logo.ico';
</script>

<div class="mt-10 w-full">
	<div class="flex flex-col">
		<div class="flex w-full items-center justify-center">
			<img src={logo} alt="logo" height="120px" width="120px" />
		</div>
	</div>
	<slot />
</div>
