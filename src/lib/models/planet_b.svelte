<script>
    import { GLTF, interactivity, Float} from '@threlte/extras'
    interactivity()
    let rate = 0.2
</script>
<Float speed={5*rate} rotationSpeed={5*rate} rotationIntensity={6*rate} floatIntensity={5*rate}>
<GLTF 
    url="/models/lowpoly_planet.glb"
    position={[-2, 3, 7]}
    scale={0.005}
    interactive 
    on:click={() => {
        console.log('User clicked!')
    }}
/>
</Float>