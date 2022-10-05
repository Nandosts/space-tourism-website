<script lang="ts">
	import { data } from '$lib/modules/translation/data.svelte';
	import type { dataType } from '$lib/modules/translation/data.svelte';

	import { _ } from 'svelte-i18n';

	let technology = ($data as dataType).technology || [];
	$: technology = ($data as dataType).technology || [];

	let SelectedTechnology = technology ? technology[0] : undefined;

	function setSelected(num: number) {
		SelectedTechnology = technology[num];
	}

	$: if (technology) {
		setSelected(0);
	}
</script>

<div class="wrapper">
	<div class="content">
		<h5 class="global-head-5 content-title">
			<b class="title-number">03</b>
			{$_('technologyTitle')}
		</h5>
		<div class="technology-container">
			<picture>
				<source media="(min-width: 1280px)" srcset={SelectedTechnology?.images.portrait} />
				<img src={SelectedTechnology?.images.landscape} alt="Flowers" />
			</picture>
		</div>
		<div class="text-container">
			<div class="select-technology">
				{#each technology as technology, i}
					<div
						class="selection-ball global-nav-text"
						class:active={SelectedTechnology === technology}
						on:click={() => setSelected(i)}
					>
						{i + 1}
					</div>
				{/each}
			</div>
			<div class="technology-data">
				<h2 class="global-sub-head-2 technology-role">{$_('technologySubtitle')}</h2>
				<h2 class="global-head-3">
					{SelectedTechnology?.name}
				</h2>
				<p class="technology-description">
					{SelectedTechnology?.description}
				</p>
			</div>
		</div>
	</div>
</div>

<style lang="scss">
	@use 'src/routes/styles/sizes.scss' as v;

	.wrapper {
		@media only screen and (min-width: v.$mobile-devices) {
			--background-image: url('../../assets/technology/background-technology-mobile.jpg');

			--content-grid-area: 'title' 'img' 'content-text';
			--content-grid-columns: 1fr;
			--text-container-columns: 1fr;

			--content-text-align: center;
			--select-technology-direction: row;
		}

		@media only screen and (min-width: v.$tablet-devices) {
			--background-image: url('../../assets/technology/background-technology-tablet.jpg');
		}

		@media only screen and (min-width: v.$md-desktop-devices) {
			--background-image: url('../../assets/technology/background-technology-desktop.jpg');

			--content-grid-area: 'title img' 'content-text img';
			--content-grid-columns: 1fr 1fr;
			--text-container-columns: auto 1fr;

			--content-text-align: start;
			--select-technology-direction: column;
		}

		display: grid;

		background-image: var(--background-image);
		background-size: cover;
		background-repeat: no-repeat;

		min-height: 100vh;
		.content {
			display: grid;

			margin-top: 4rem;

			row-gap: 1rem;
			grid-template-areas: var(--content-grid-area);
			grid-template-columns: var(--content-grid-columns);
			text-align: var(--content-text-align);

			place-items: center;
		}

		.content-title {
			grid-area: title;
			.title-number {
				opacity: 0.25;
			}
		}

		.technology-container {
			height: 100%;
			display: flex;
			align-items: center;
			grid-area: img;

			img {
				width: 100%;
				max-width: 100vw;
				max-height: 85vh;
			}
		}

		.text-container {
			width: min(28rem, 100%);
			height: 80%;
			display: grid;
			grid-template-columns: var(--text-container-columns);
			justify-items: center;
			gap: 2rem;
			grid-area: content-text;

			.select-technology {
				display: flex;

				flex-direction: var(--select-technology-direction);

				gap: 1rem;

				.selection-ball {
					position: relative;

					display: flex;
					align-items: center;
					justify-content: center;

					height: 5rem;
					width: 5rem;
					background-color: transparent;
					border: 1px solid var(--global-grey);
					color: var(--global-grey);
					font-size: 3rem;
					border-radius: 50%;

					transition: all 0.3s ease-in-out 0s;

					&:hover {
						cursor: pointer;
						background-color: var(--global-grey);
						color: var(--global-dark);
					}

					&.active {
						background-color: var(--global-white);
						color: var(--global-dark);
					}
				}

				.technology-data {
					margin-bottom: auto;
					display: grid;
					row-gap: 2rem;
				}
			}

			.technology-description {
				color: var(--global-grey);
			}
		}
	}
</style>
