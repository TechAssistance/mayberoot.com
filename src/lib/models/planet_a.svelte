<script>
    import { GLTF, interactivity, Float} from '@threlte/extras'
    interactivity()
    let rate = 0.2
</script>
<Float speed={5*rate} rotationSpeed={5*rate} rotationIntensity={6*rate} floatIntensity={5*rate}>
<GLTF 
    url="/models/low-poly-planet.glb"
    position={[-20, -17, 2]}
    scale={0.5}
    interactive 
    on:click={() => {
        console.log('User clicked!')
    }}
/>
</Float>