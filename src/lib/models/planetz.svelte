<script>
    import { GLTF, interactivity, Float} from '@threlte/extras'
    interactivity()
    let rate = 0.2
</script>



<Float speed={5*rate} rotationSpeed={5*rate} rotationIntensity={6*rate} floatIntensity={5*rate}>
    <GLTF 
    url="/models/planetz.glb"
    position={[2, -7, 10]}
    scale={0.5}
    interactive 
    on:click={() => {
        console.log('User clicked!')
    }}
/>
</Float>