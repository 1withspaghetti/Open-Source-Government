<script lang="ts">
  import { Canvas } from '@threlte/core'
  import { Project, Sheet, Studio } from '@threlte/theatre'
  import Scene from './Scene.svelte'
  import { dev } from '$app/environment'
  import state from '$lib/animations/Open Source Government.theatre-project-state.json'
  import '$lib/app.css'
  import { type ISheet } from '@theatre/core';

  let sheet: ISheet;

  let isDev = dev && false;

  const onScroll = () => {
    if (!isDev) sheet.sequence.position = window.scrollY / (document.body.scrollHeight - window.innerHeight) * 4;
  }

  // onChange(sheet.sequence.pointer.position, (value) => {
  //   window.scrollTo(0, value * (document.body.scrollHeight - window.innerHeight) / 4);
  // });
</script>
<svelte:document on:scroll={onScroll} />

<Studio enabled={isDev} />

<Canvas>
  <Project name="Open Source Government" config={{ state }} >
    <Sheet bind:sheet>
      <Scene {isDev} />
    </Sheet>
  </Project>
</Canvas>
