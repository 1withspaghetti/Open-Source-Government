<script lang="ts">
  import { T } from '@threlte/core'
  import { ContactShadows, Float, Grid, OrbitControls } from '@threlte/extras'
  import { SheetObject } from '@threlte/theatre'
  import VotingMachine from './models/voting_machine.svelte';
  import ComputerRoom from './models/computer_room.svelte';
  import Desk from './models/Desk.svelte';
  import { VideoTexture } from 'three';

  export let isDev = false;
  
  let orbitControls = isDev && false;

  let videoEl: HTMLVideoElement;

  function rad(deg: number) {
    return deg * Math.PI / 180;
  }
</script>

{#if orbitControls}
  <T.PerspectiveCamera
    makeDefault
    position={[-10, 10, 10]}
  >
    <OrbitControls
      enableZoom={true}
      enableDamping
      target.y={1.5}
    />
  </T.PerspectiveCamera>
{/if}

<SheetObject
  key="Camera"
  let:Transform
>
  <Transform>
    <T.PerspectiveCamera
      makeDefault={!orbitControls}
      position={[0, 0, 0]}
    >
    </T.PerspectiveCamera>
  </Transform>
</SheetObject>

<T.AmbientLight intensity={0.4} />

{#if isDev}
  <Grid
    position.y={-0.001}
    cellColor="#ffffff"
    sectionColor="#ffffff"
    sectionThickness={0}
    fadeDistance={50}
    cellSize={2}
  />
{/if}

<ContactShadows
  scale={10}
  blur={2}
  far={2.5}
  opacity={0.5}
/>

<T.DirectionalLight
  intensity={0.5}
  position.x={5}
  position.y={20}
  position.z={10}
/>
<Float
  floatIntensity={1}
  floatingRange={[0, 1]}
>
  <VotingMachine />
</Float>

<T.DirectionalLight
  intensity={0.5}
  position.x={-20}
  position.y={10}
  position.z={40}
/>
<ComputerRoom position={[ -20, 0.25, 40]} />

<video bind:this={videoEl} id="video01" loop autoplay crossOrigin="anonymous" playsinline style="display:none" src="/videos/vecteezy_animation-of-digital-data-moving-on-back-background_51579650.webm"></video>
<Desk position={[-11, -11, 13]} rotation={[0, rad(-39), 0]} />
<T.Mesh position={[-12.5, -11, 15]} rotation={[rad(20), rad(141), rad(-13)]}>
  <T.BoxGeometry attach="geometry" args={[16/2, 9/2, 0]} />
  {#if videoEl}
    <T.MeshBasicMaterial attach="material" map={new VideoTexture(videoEl)} transparent opacity={0.1} />
  {:else}
    <T.MeshBasicMaterial attach="material" color="red" />
  {/if}
</T.Mesh>
