<script lang="ts">
    import { T, useFrame, useThrelte } from '@threlte/core'
    import * as Extra from '@threlte/extras'
    import * as Three from 'three'
    import * as Utils from 'three/src/math/MathUtils'
    import { Grid, MeshLineGeometry, MeshLineMaterial, OrbitControls, useGltf, useGltfAnimations } from '@threlte/extras'
    import { useRender } from '@threlte/core'
    
    import { interactivity, Text, useCursor } from '@threlte/extras'
    import { DEG2RAD } from 'three/src/math/MathUtils'
    
    let sum = 0;
    //coffee
    let coffeeScale = 0.3;
    let coffeePressed = false;
    //cake
    let cakeScale = 0.3;
    let cakePressed = false;
    //farikal
    let farikalScale = 0.3;
    let farikalPressed = false;
    //saft
    let saftScale = 0.15;
    let saftPressed = false;

    const { hovering, onPointerLeave } = useCursor()

    //coffee
    function onCoffeePointerDown() {
        coffeeScale = 0.32;
        coffeePressed = true;
    }

    function onCoffeePointerUp() {
        if (coffeePressed) {
            console.log("coffee");
            sum += 15;
            coffeePressed = false;
        }
        
        coffeeScale = 0.3;
    }

    //cake
    function onCakePointerDown() {
        cakeScale = 0.32;
        cakePressed = true;
    }

    function onCakePointerUp() {
        if  (cakePressed) {
            console.log("cake");
            sum += 20;
            cakePressed = false;
        }
        
        cakeScale = 0.3
    }

    //farikal
    function onFarikalPointerDown() {
        farikalScale = 0.32;
        farikalPressed = true;
    }

    function onFarikalPointerUp() {
        if  (farikalPressed) {
            console.log("farikal");
            sum += 25;
            farikalPressed = false;
        }
        
        farikalScale = 0.3
    }
    
    //saft
    function onSaftPointerDown() {
        saftScale = 0.17;
        saftPressed = true;
    }

    function onSaftPointerUp() {
        if  (saftPressed) {
            console.log("saft");
            sum += 15;
            saftPressed = false;
        }
        
        saftScale = 0.15
    }

    $: color = $hovering ? '#dddddd' : '#FE3D00'
    $: myscale = $hovering ? 0.32 : 0.3


    const { size } = useThrelte()
    let zoom = $size.width / 7
    $: zoom = $size.width / 7

    
    interactivity()
</script>

<T.PerspectiveCamera
        makeDefault
        position={[0, 4, 7]}
        target={[0, 2, 0]}
        rotation={[0, 40, 0]}
        on:create={({ ref }) => {
            ref.lookAt(0, 2, 0)
          }}
    >
        <OrbitControls
        enableDamping
        target={[0, 2, 0]}
        />

</T.PerspectiveCamera>

<!-- <Grid
    gridSize={[10, 10]}
    cellColor={'#ffffff'}
    sectionThickness={1}
/> -->

<Text
  text="Sum: {sum},- kr
  Vipps til 94977556"
  interactive
  fontSize={0.25}
  anchorY="100%"
  anchorX="50%"
  rotation.y={0 * DEG2RAD}
  position.y={4.1}
  position.x={2}
  {color}
/>

<Text
  text="
  15,-

  25,-

  20,-

  15,-"
  interactive
  fontSize={0.45}
  anchorY="100%"
  anchorX="50%"
  rotation.y={0 * DEG2RAD}
  position={[-2, 0.9, 0.27]}
  color=grey
/>

<Extra.GLTF
    url="models/cupofcoffealasverre.glb"
    interactive
    on:pointerdown={onCoffeePointerDown}
    on:pointerup={onCoffeePointerUp}
    position={[-0.82, 0, 0]}
    scale={coffeeScale}
    castShadow
    receiveShadow
/>

<Extra.GLTF
    url="models/kake.glb"
    interactive
    on:pointerdown={onCakePointerDown}
    on:pointerup={() => onCakePointerUp()}
    position={[-0.6, 1.6, 0.27]}
    scale={cakeScale}
    rotation={[-1.6, 0, -2]}
    castShadow
    receiveShadow
    autoRotate
/>

<Extra.GLTF
    url="models/Farikal.glb"
    interactive
    on:pointerdown={onFarikalPointerDown}
    on:pointerup={() => onFarikalPointerUp()}
    position={[-0.95, 2.8, 0.27]}
    scale={farikalScale}
    rotation={[-1.6, 0, -2]}
    castShadow
    receiveShadow
/>

<Extra.GLTF
    url="models/saft.glb"
    interactive
    on:pointerdown={onSaftPointerDown}
    on:pointerup={() => onSaftPointerUp()}
    position={[-0.95, 3.75, 0.27]}
    scale={saftScale}
    rotation={[-1.6, 0, -2]}
    castShadow
    receiveShadow
/>



<T.DirectionalLight
    position={[6, 15, 7]}
    on:create={({ ref }) => {
        ref.lookAt(0, 2, 0)
        }}
    intensity={9}
/>

<T.AmbientLight 
    intensity={0} 
/>