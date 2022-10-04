<script lang="ts">
	import Data from '../data.json';

	const destinations = Data.destinations;
	let SelectedDestination = destinations[0];

	function setSelected(num: number) {
		SelectedDestination = destinations[num];
	}
</script>

<div class="wrapper">
	<div class="content">
		<div class="planet-container">
			<h5 class="global-head-5"><b class="title-number">01</b> Pick your Destination</h5>
			<img
				src={SelectedDestination.images.png}
				width={350}
				height={350}
				alt={'Imagem de ' + SelectedDestination.name}
			/>
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
				{SelectedDestination.name}
			</h2>
			{SelectedDestination.description}

			<div class="planet-data">
				<div>
					<p class="global-nav-text planet-data-title">AVG. DISTANCE</p>
					<p class="global-sub-head-1">{SelectedDestination.distance}</p>
				</div>

				<div>
					<p class="global-nav-text planet-data-title">EST. TRAVEL TIME</p>
					<p class="global-sub-head-1">{SelectedDestination.travel}</p>
				</div>
			</div>
		</div>
	</div>
</div>

<style lang="scss">
	@use 'src/routes/styles/sizes.scss' as v;

	.wrapper {
		@media only screen and (min-width: v.$mobile-devices) {
			--background-image: url('src/assets/destination/background-destination-mobile.jpg');
			--content-grid-columns: 1fr;
			--content-text-align: center;
		}

		@media only screen and (min-width: v.$tablet-devices) {
			--background-image: url('src/assets/destination/background-destination-tablet.jpg');
		}

		@media only screen and (min-width: v.$md-desktop-devices) {
			--background-image: url('src/assets/destination/background-destination-desktop.jpg');
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

					&:hover {
						cursor: pointer;
					}

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

					&:hover:before {
						cursor: pointer;
						visibility: visible;
						transform: scaleX(1);
					}

					&.active:before {
						visibility: visible;
						transform: scaleX(1);
						background-color: var(--global-white);
					}
				}
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
