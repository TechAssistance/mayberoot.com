<script>
    import { GLTF, interactivity, Float} from '@threlte/extras'
    interactivity()
    let rate = 0.2
</script>
<Float speed={5*rate} rotationSpeed={5*rate} rotationIntensity={6*rate} floatIntensity={5*rate}>
<GLTF 
    url="/models/destroyed_moon.glb"
    position={[8.5, 1.5,-1.8]}
    scale={0.3}
    interactive 
    on:click={() => {
        console.log('User clicked!')
    }}
/>
</Float>