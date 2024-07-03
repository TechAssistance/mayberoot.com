<script>
    import { GLTF, interactivity, Float} from '@threlte/extras'
    interactivity()
    let rate = 0.2
</script>



<Float speed={5*rate} rotationSpeed={5*rate} rotationIntensity={6*rate} floatIntensity={5*rate}>
    <GLTF 
    url="/models/space_exploration_wlp_series_8.glb"
    position={[15, -4, -10]}
    scale={0.2}
    interactive 
    on:click={() => {
        console.log('User clicked!')
    }}
/>
</Float>