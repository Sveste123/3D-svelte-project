<script lang="ts">
    import { Pane } from 'tweakpane'
    import { browser } from '$app/environment'

    import { Canvas, T } from '@threlte/core'
    import Scene from '../components/scene.svelte'

    let pointLight = {
        position: { x: 0, y: 2, z: 2 },
        color: 'hsl(60, 100%, 50%)',
    }

    let ghost = {
        position: { x: 0, y: 1.9, z: 0 },
        scale: 0.4,
    }

    function gotoVipps() {
      window.location.href = "https://qr.vipps.no/28/2/01/031/4794977556?v=1";
    }

</script>

<div class="title">
  Velkommen til 2MDA Kafé
</div>

<div class="undertitle">
  Legg sammen varene først ved å trykke på dem, 
</div>
<div class="undertitle">
  da går det kjappere fremme i 2MDA-Kaféen😉,
</div>
<div class="undertitle">
  TIPS: last inn siden på nytt for å resette
</div>
<div class="center">
  <button class="centerButton" on:click={gotoVipps}>Gå til VIPPS</button>
</div>
<Canvas rendererParameters={{ antialias: false }}>
    <Scene/>
</Canvas>



<div class="watermark">Inntektene går til gode hensikter for 2MDA - Nettside laget av Sverre
 
</div>

<!-- <script lang="ts">
    import { Canvas } from '@threlte/core'
    import { T, useFrame } from '@threlte/core'
    import { Instance, InstancedMesh } from '@threlte/extras'
    let dn = Date.now()
    useFrame(() => (dn = Date.now()))
  </script>

  <Canvas>
      <InstancedMesh>
        <T.SphereGeometry args={[0.5]} />
        <T.MeshStandardMaterial color="white" />
        <Instance
          position.x={-2}
          position.y={Math.sin(dn / 1000 + 40)}
        />
        <Instance
          position.x={-1}
          position.y={Math.sin(dn / 1000 + 10)}
        />
        <Instance
          position.x={0}
          position.y={Math.sin(dn / 1000 + 5)}
        />
        <Instance
          position.x={1}
          position.y={Math.sin(dn / 1000 + 200)}
        />
        <Instance
          position.x={2}
          position.y={Math.sin(dn / 1000 + 550)}
        />
      </InstancedMesh>
      <T.DirectionalLight
        position.y={10}
        position.z={5}
      />
      <T.AmbientLight intensity={0.1} />
  </Canvas> -->


<style>
  .title {
    color:orange;
    font-size: 2em;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    text-align: center;
  }

  .undertitle {
    color:white;
    font-size: 1.2em;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    text-align: center;
  }
  .center {
    text-align: center;
  }

  .centerButton {
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    font-size: 2em;
  }

  .watermark {
    position: fixed;
    bottom: 5px;
    left: 7px;
    font-size: 23px;
    color: #999;
    text-align: center;
    border-top: none;
  }
</style>