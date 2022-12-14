<script lang="ts">
	import { data } from '$lib/modules/translation/data.svelte';
	import type { dataType } from '$lib/modules/translation/data.svelte';

	import { _ } from 'svelte-i18n';

	let destinations = ($data as dataType).destinations || [];

	$: destinations = ($data as dataType).destinations || [];
	let SelectedDestination = destinations ? destinations[0] : undefined;

	function setSelected(num: number) {
		SelectedDestination = destinations ? destinations[num] : undefined;
	}

	$: if (destinations) {
		setSelected(0);
	}
</script>

<div class="wrapper">
	<div class="content">
		<div class="planet-container">
			<h5 class="global-head-5"><b class="title-number">01</b> {$_('destinationTitle')}</h5>
			<picture>
				<source
					srcset={SelectedDestination?.images.png}
					type="image/png"
					alt={'Imagem de ' + SelectedDestination?.name}
				/>
				<img
					src={SelectedDestination?.images.webp}
					alt={'Imagem de ' + SelectedDestination?.name}
				/>
			</picture>
		</div>
		<div class="text-container">
			<div class="select-destination">
				{#each destinations as destination, i}
					<div
						class="selection-title global-nav-text"
						class:active={SelectedDestination === destination}
						on:click={() => setSelected(i)}
					>
						{destination.name}
					</div>
				{/each}
			</div>
			<h2 class="global-head-2">
				{SelectedDestination?.name}
			</h2>
			<p class="destination-description">
				{SelectedDestination?.description}
			</p>

			<div class="planet-data">
				<div>
					<p class="global-nav-text planet-data-title">{$_('destinationDistance')}</p>
					<p class="global-sub-head-1">{SelectedDestination?.distance}</p>
				</div>

				<div>
					<p class="global-nav-text planet-data-title">{$_('destinationTravel')}</p>
					<p class="global-sub-head-1">{SelectedDestination?.travel}</p>
				</div>
			</div>
		</div>
	</div>
</div>

<style lang="scss">
	@use 'src/routes/styles/sizes.scss' as v;

	.wrapper {
		@media only screen and (min-width: v.$mobile-devices) {
			--background-image: url('../../assets/destination/background-destination-mobile.jpg');
			--content-grid-columns: 1fr;
			--content-text-align: center;
		}

		@media only screen and (min-width: v.$tablet-devices) {
			--background-image: url('../../assets/destination/background-destination-tablet.jpg');
		}

		@media only screen and (min-width: v.$md-desktop-devices) {
			--background-image: url('../../assets/destination/background-destination-desktop.jpg');
			--content-grid-columns: 1fr 1fr;
			--content-text-align: start;
		}

		display: grid;
		grid-template-rows: 1fr;

		background-image: var(--background-image);
		background-size: cover;
		background-repeat: no-repeat;

		width: 100%;
		height: 100%;
		min-height: 100vh;

		.content {
			display: grid;

			margin-top: 4rem;

			grid-template-columns: var(--content-grid-columns);
			text-align: var(--content-text-align);

			place-items: center;

			width: 100%;
			overflow-x: auto;
		}
		.planet-container {
			.title-number {
				opacity: 0.25;
			}
			margin-bottom: 2rem;
		}

		.text-container {
			width: min(28rem, 100%);

			.select-destination {
				display: flex;
				justify-content: var(--content-text-align);
				gap: 1rem;

				.selection-title {
					text-transform: uppercase;
					position: relative;
					height: 2.3rem;
					color: var(--global-grey);

					&:before {
						content: '';

						position: absolute;
						bottom: 0;
						left: 0;

						width: 100%;
						height: 0.2rem;

						background-color: var(--global-grey);

						visibility: hidden;
						transform: scaleX(0);

						transition: all 0.3s ease-in-out 0s;
					}

					&:hover {
						cursor: pointer;
						&:before {
							cursor: pointer;
							visibility: visible;
							transform: scaleX(1);
						}
					}
					&.active {
						color: white;

						&:before {
							visibility: visible;
							transform: scaleX(1);
							background-color: var(--global-white);
						}
					}
				}
			}

			.destination-description {
				color: var(--global-grey);
			}

			.planet-data {
				display: flex;
				justify-content: var(--content-text-align);

				margin-top: 2rem;
				margin-left: 0;
				gap: 4rem;

				text-transform: uppercase;
				div {
					line-height: 2.5rem;
					.planet-data-title {
						color: var(--global-grey);
					}
				}
			}
		}
	}
</style>
