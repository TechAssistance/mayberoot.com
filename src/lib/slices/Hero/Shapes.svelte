<script lang="ts">


import {T as Threlte} from '@threlte/core';
import * as THREE from 'three';
import Geometry from './Geometry.svelte';
	import { ContactShadows, Environment, interactivity, transitions } from '@threlte/extras';
	import { blur } from 'svelte/transition';
  import { OrbitControls, Grid, Stars, useGltf } from '@threlte/extras'
  import DestroyedMoon from "$lib/models/destroyed_moon.svelte";
  import PlanetSat from '$lib/models/planet_sat.svelte';
	import PlanetA from '$lib/models/planet_a.svelte';
	import PlanetB from '$lib/models/planet_b.svelte';
	import PlanetExplore from '$lib/models/planet_explore.svelte';
	import Planetz from '$lib/models/planetz.svelte';

  interactivity()
  transitions()
</script>


<!-- <Stars speed ={0.5} lightness={0.8} radius={120}/> -->

<Threlte.PerspectiveCamera
makeDefault
position.y={1}
position.z={15}
fov={100}
on:create={({ ref }) => {
  ref.lookAt(0, 2, 2,)
}}
>
  <OrbitControls
    enableDamping
    enablePan={false}
    enableZoom={false}
    autoRotate
  />
</Threlte.PerspectiveCamera>



<Environment files="outside.hdr" path="/" format="hdr" />
<Threlte.AmbientLight />
<!-- <ContactShadows position={[0,-3.5,0]} opacity={0.65} scale={40} blur={1} far={9} /> -->
<!-- Gem -->
<Geometry position={[0, 0, 0]} rate={0.3} geometry={new THREE.IcosahedronGeometry(3)} />

<!-- Pill -->
<Geometry
	position={[1, 1.5, -0.5]}
	rate={0.4}
	geometry={new THREE.CapsuleGeometry(0.5, .6, 2, 16)}
/>

<!-- Soccer Ball -->
<Geometry position={[2.5, -1, 1.2]} rate={0.6} geometry={new THREE.DodecahedronGeometry(1.5)} />

<!-- Donut -->
<Geometry
	position={[4, 2.0, -1.5]}
	rate={0.5}
	geometry={new THREE.TorusGeometry(0.6, 0.25, 16, 32)}
/>

<!-- Diamond -->
<Geometry position={[5.5, -2.5, 0.8]} rate={0.7} geometry={new THREE.OctahedronGeometry(1.5)} />


<DestroyedMoon />
<PlanetSat />
<PlanetA />
<PlanetB />
<PlanetExplore />
<Planetz />