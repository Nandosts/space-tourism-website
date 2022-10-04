<script lang="ts">
	import { data } from '../data.svelte';

	const crew = data.crew;
	let SelectedCrew = crew[0];

	function setSelected(num: number) {
		SelectedCrew = crew[num];
	}
</script>

<div class="wrapper">
	<div class="content">
		<h5 class="global-head-5 content-title"><b class="title-number">02</b> Meet your Crew</h5>
		<div class="crew-container">
			<img src={SelectedCrew.images.png} alt={'Imagem de ' + SelectedCrew.name} />
		</div>
		<div class="text-container">
			<div class="crew-data">
				<h2 class="global-head-4 crew-role">
					{SelectedCrew.role}
				</h2>
				<h2 class="global-head-3">
					{SelectedCrew.name}
				</h2>
				<p class="crew-description">
					{SelectedCrew.bio}
				</p>
			</div>

			<div class="select-crew">
				{#each crew as crew, i}
					<div
						class="selection-ball global-nav-text"
						class:active={SelectedCrew === crew}
						on:click={() => setSelected(i)}
					/>
				{/each}
			</div>
		</div>
	</div>
</div>

<style lang="scss">
	@use 'src/routes/styles/sizes.scss' as v;

	.wrapper {
		@media only screen and (min-width: v.$mobile-devices) {
			--background-image: url('../../assets/crew/background-crew-mobile.jpg');
			--content-grid-area: 'title' 'img' 'content-text';
			--content-grid-columns: 1fr;
			--content-text-align: center;
		}

		@media only screen and (min-width: v.$tablet-devices) {
			--background-image: url('../../assets/crew/background-crew-tablet.jpg');
		}

		@media only screen and (min-width: v.$md-desktop-devices) {
			--background-image: url('../../assets/crew/background-crew-desktop.jpg');
			--content-grid-area: 'title img' 'content-text img';
			--content-grid-columns: 1fr 1fr;
			--content-text-align: start;
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

		.crew-container {
			height: 100%;
			display: flex;
			align-items: flex-end;
			grid-area: img;

			img {
				width: 100%;
				max-height: 80vh;
			}
		}

		.text-container {
			width: min(28rem, 100%);
			height: 80%;
			display: grid;
			grid-template-rows: 1fr auto;
			grid-area: content-text;

			.crew-data {
				margin-bottom: auto;
				display: grid;
				row-gap: 2rem;
			}

			.select-crew {
				display: flex;
				justify-content: var(--content-text-align);
				margin-top: 3rem;
				gap: 1rem;

				.selection-ball {
					text-transform: uppercase;
					position: relative;
					height: 1rem;
					width: 1rem;
					background-color: var(--global-white);
					opacity: 0.17;
					content: '';
					border-radius: 50%;

					transition: all 0.3s ease-in-out 0s;

					&:hover {
						cursor: pointer;
						opacity: 0.5;
					}
					&.active {
						background-color: var(--global-white);
						opacity: 1;
					}
				}
			}

			.crew-description {
				color: var(--global-grey);
			}
		}
	}
</style>
