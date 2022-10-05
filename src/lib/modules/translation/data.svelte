<script lang="ts" context="module">
	import { onMount } from 'svelte';

	import { writable } from 'svelte/store';
	import { _ } from 'svelte-i18n';

	import EuropaPng from '../../../assets/destination/image-europa.png';
	import EuropaWebp from '../../../assets/destination/image-europa.webp';
	import MoonPng from '../../../assets/destination/image-moon.png';
	import MoonWebp from '../../../assets/destination/image-moon.webp';
	import MarsPng from '../../../assets/destination/image-mars.png';
	import MarsWebp from '../../../assets/destination/image-mars.webp';
	import TitanPng from '../../../assets/destination/image-titan.png';
	import TitanWebp from '../../../assets/destination/image-titan.webp';

	import AnoushehAnsariPng from '../../../assets/crew/image-anousheh-ansari.png';
	import AnoushehAnsariWebp from '../../../assets/crew/image-anousheh-ansari.webp';
	import DouglasHurleyPng from '../../../assets/crew/image-douglas-hurley.png';
	import DouglasHurleyWebp from '../../../assets/crew/image-douglas-hurley.webp';
	import MarkShuttleworthPng from '../../../assets/crew/image-mark-shuttleworth.png';
	import MarkShuttleworthWebp from '../../../assets/crew/image-mark-shuttleworth.webp';
	import VictorGloverPng from '../../../assets/crew/image-victor-glover.png';
	import VictorGloverWebp from '../../../assets/crew/image-victor-glover.webp';

	import LaunchVehicleLandscape from '../../../assets/technology/image-launch-vehicle-landscape.jpg';
	import LaunchVehiclePortrait from '../../../assets/technology/image-launch-vehicle-portrait.jpg';
	import SpaceCapsuleLandscape from '../../../assets/technology/image-space-capsule-landscape.jpg';
	import SpaceCapsulePortrait from '../../../assets/technology/image-space-capsule-portrait.jpg';
	import SpaceportLandscape from '../../../assets/technology/image-spaceport-landscape.jpg';
	import SpaceportPortrait from '../../../assets/technology/image-spaceport-portrait.jpg';

	type TDestination = {
		name: string;
		images: {
			png: string;
			webp: string;
		};
		description: string;
		distance: string;
		travel: string;
	};

	type TCrew = {
		name: string;
		images: {
			png: string;
			webp: string;
		};
		role: string;
		bio: string;
	};

	type TTechnology = {
		name: string;
		images: {
			portrait: string;
			landscape: string;
		};
		description: string;
	};

	export type dataType = {
		destinations?: TDestination[];
		crew?: TCrew[];
		technology?: TTechnology[];
	};

	export let data = writable({});
	export let setData = () => undefined as unknown;
</script>

<script lang="ts">
	setData = () => {
		data.set({
			destinations: [
				{
					name: $_('moonName'),
					images: {
						png: MoonPng,
						webp: MoonWebp
					},
					description: $_('moonDescription'),
					distance: $_('moonDistance'),
					travel: $_('moonTravel')
				},
				{
					name: $_('marsName'),
					images: {
						png: MarsPng,
						webp: MarsWebp
					},
					description: $_('marsDescription'),
					distance: $_('marsDistance'),
					travel: $_('marsTravel')
				},
				{
					name: $_('europaName'),
					images: {
						png: EuropaPng,
						webp: EuropaWebp
					},
					description: $_('europaDescription'),
					distance: $_('europaDistance'),
					travel: $_('europaTravel')
				},
				{
					name: $_('titanName'),
					images: {
						png: TitanPng,
						webp: TitanWebp
					},
					description: $_('titanDescription'),
					distance: $_('titanDistance'),
					travel: $_('titanTravel')
				}
			],
			crew: [
				{
					name: $_('douglasName'),
					images: {
						png: DouglasHurleyPng,
						webp: DouglasHurleyWebp
					},
					role: $_('douglasRole'),
					bio: $_('douglasBio')
				},
				{
					name: $_('markName'),
					images: {
						png: MarkShuttleworthPng,
						webp: MarkShuttleworthWebp
					},
					role: $_('markRole'),
					bio: $_('markBio')
				},
				{
					name: $_('victorName'),
					images: {
						png: VictorGloverPng,
						webp: VictorGloverWebp
					},
					role: $_('victorRole'),
					bio: $_('victorBio')
				},
				{
					name: $_('anoushehName'),
					images: {
						png: AnoushehAnsariPng,
						webp: AnoushehAnsariWebp
					},
					role: $_('anoushehRole'),
					bio: $_('anoushehBio')
				}
			],
			technology: [
				{
					name: $_('launchName'),
					images: {
						portrait: LaunchVehiclePortrait,
						landscape: LaunchVehicleLandscape
					},
					description: $_('launchDescription')
				},
				{
					name: $_('spaceportName'),
					images: {
						portrait: SpaceportPortrait,
						landscape: SpaceportLandscape
					},
					description: $_('spaceportDescription')
				},
				{
					name: $_('spaceCapsuleName'),
					images: {
						portrait: SpaceCapsulePortrait,
						landscape: SpaceCapsuleLandscape
					},
					description: $_('spaceCapsuleDescription')
				}
			]
		} as dataType);
	};

	onMount(() => setData());
</script>
