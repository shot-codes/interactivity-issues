<script lang="ts">
  import { T } from "@threlte/core";
  import { interactivity, Float } from "@threlte/extras";
  import { MeshStandardMaterial, Color } from "three";
  import { onDestroy } from "svelte";
  import { spring } from "svelte/motion";

  export let position: [number, number, number] = [0, 0, 0];

  interactivity();
  const scale = spring(1);
  const floatIntensity = spring(1);

  const red = new Color(0xfe3d00);
  const blue = new Color(0x0000ff);

  let material = new MeshStandardMaterial({
    color: red,
  });

  onDestroy(() => {
    material.dispose();
  });
</script>

<Float
  floatIntensity={$floatIntensity}
  floatingRange={[
    [-0.5, 0.5],
    [0, 1],
    [-0.5, 0.5],
  ]}
  rotationIntensity={0.15}
  rotationSpeed={2}
>
  <T.Mesh
    {position}
    {material}
    scale={$scale}
    on:click={(e) => {
      e.stopPropagation();
      console.log("test");
    }}
    on:pointerenter={(e) => {
      e.stopPropagation();
      scale.set(1.2);
      material.color = blue;
    }}
    on:pointerleave={(e) => {
      e.stopPropagation();
      scale.set(1);
      material.color = red;
    }}
    castShadow
  >
    <T.SphereGeometry args={[1, 32, 32]} />
  </T.Mesh>
</Float>
