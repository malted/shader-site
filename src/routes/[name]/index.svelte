<script>
	import { page } from "$app/stores";

	// @ts-ignore
	import previewData from "/static/previews/previewData.json";

	const current = previewData.find(element => element.nameShort === $page.params.name);

</script>

<svelte:head>
	<!-- Primary Meta Tags -->
	<title>{current.name}</title>
	<meta name="title" content="{current.name}">
	<meta name="description" content="Malted's {current.name} shader (#{(previewData.indexOf(current) + 1).toString().padStart(3, '0')})">

	<!-- Open Graph / Facebook -->
	<meta property="og:type" content="website">
	<meta property="og:url" content="https://shaders.malted.dev/{current.nameShort}">
	<meta property="og:title" content="{current.name}">
	<meta property="og:description" content="Malted's {current.name} shader (#{(previewData.indexOf(current) + 1).toString().padStart(3, '0')})">
	<meta property="og:image" content={current.cdn}>

	<!-- Twitter -->
	<meta property="twitter:card" content="summary_large_image">
	<meta property="twitter:url" content="https://shaders.malted.dev/{current.nameShort}">
	<meta property="twitter:title" content="{current.name}">
	<meta property="twitter:description" content="Malted's {current.name} shader (#{(previewData.indexOf(current) + 1).toString().padStart(3, '0')})">
	<meta property="twitter:image" content={current.cdn}>
</svelte:head>

<a href="..">
	<img 
		class="container back"
		src="/icons/arrow_back_black_24dp.svg" 
		alt="back" 
	/>
</a>

<iframe 
	title="Shaderpark iframe" 
	src="https://shaderpark.com/embed/-{current.id}" 
	frameborder="0">
</iframe>

<div class="container info">
	<h1>{current.name}</h1>
	<h2>#{(previewData.indexOf(current) + 1).toString().padStart(3, '0')}</h2>
</div>

<style>
	iframe {
		width: 99vw;
		height: 99vh;
	}

	.container {
		position: absolute;
		left: 0;
		margin: 2rem;
		user-select: none;
	}
	@media (max-width: 600px) {
		.container {
			margin: 1rem;
		}
	}
	@media (min-width: 1800px) {
		.container {
			margin: 3rem;
		}
	}
	.container.back {
		top: 0;
	}
	.container.info {
		bottom: 0;
	}

	h1 {
		font-size: 3rem;
		margin-bottom: 0rem;
	}
	h2 {
		font-size: 2.5rem;
		margin: 0;
		font-weight: 100;
	}

	img {
		height: 2rem;
		filter: invert(100%);
	}
</style>