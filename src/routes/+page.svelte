<script>
  import { Canvas } from "@threlte/core";
  import Scene from "$lib/components/scene1/Scene1.svelte";
  import { dev } from "$app/environment";
</script>

<div>
  <Canvas>
    <Scene />
  </Canvas>
</div>

<style>
  div {
    width: 100vw;
    height: 100vh;
  }
</style>
