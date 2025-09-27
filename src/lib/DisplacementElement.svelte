<script lang="ts">  
  import { getDisplacementFilter, type DisplacementOptions } from "./getDisplacementFilter";
  
  import displacementMapUri from '/src/assets/displacement.png?inline';
    console.log(displacementMapUri)

  export let className: string = '';
  export let height: number;
  export let width: number;
  export let depth: number;
  export let radius: number;
  export let strength: number;
  export let chromaticAberration: number;
  export let blur: number = 2;

  $: displacementFilterUrl = getDisplacementFilter(
    {
      height,
      width,
      radius,
      depth,
      strength,
      chromaticAberration,
    } as DisplacementOptions,
    displacementMapUri
  );

  $: backdropFilterStyle = `blur(${blur / 2}px) url('${displacementFilterUrl}') blur(${blur}px) brightness(1.1) saturate(1.5)`;
</script>

<div
  class="{className}"
  style:height="{height}px"  
  style:border-radius="{radius}px"
  style:backdrop-filter={backdropFilterStyle}
>
  <slot />
</div>