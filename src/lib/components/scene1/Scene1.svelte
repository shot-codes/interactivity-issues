<script lang="ts">
  import { T } from "@threlte/core";
  import { Float } from "@threlte/extras";
  import { OrbitControls } from "@threlte/extras";
  import { DEG2RAD } from "three/src/math/MathUtils";
  import Blob from "$lib/components/scene1/Blob.svelte";
</script>

<T.PerspectiveCamera
  makeDefault
  position={[0, 5, 10]}
  on:create={({ ref }) => {
    ref.lookAt(0, 1, 0);
  }}
>
  <OrbitControls enableDamping maxPolarAngle={85 * DEG2RAD} minPolarAngle={10 * DEG2RAD} />
</T.PerspectiveCamera>

<T.DirectionalLight castShadow position={[3, 10, 7]} />
<T.AmbientLight intensity={0.1} />

<T.Mesh rotation.x={-90 * DEG2RAD} receiveShadow>
  <T.CircleGeometry args={[1000, 1000]} />
  <T.MeshStandardMaterial color="white" />
</T.Mesh>

<Blob position={[0, 2, 0]} />
<Blob position={[3, 2, 0]} />
<Blob position={[-3, 2, 0]} />
