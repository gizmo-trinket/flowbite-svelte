<script lang="ts">
  import type { SVGAttributes } from 'svelte/elements';
  interface $$Props extends SVGAttributes<SVGSVGElement>{
    size?: string;
    variation?: 'solid' | 'outline';
    ariaLabel?: string;
  }
  
  export let size: $$Props['size'] = '24';
  export let variation: $$Props['variation'] = 'outline';
  export let ariaLabel: $$Props['ariaLabel'] = 'bars 3';

  let viewBox: string;
  let svgpath: string;
  let svgoutline = `<path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16"></path> `;
  let svgsolid = `<path clip-rule="evenodd" fill-rule="evenodd" d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 10a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 15a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1z"></path> `;
  $: switch (variation) {
    case 'outline':
      svgpath = svgoutline;
      viewBox = '0 0 24 24';
      break;
    case 'solid':
      svgpath = svgsolid;
      viewBox = '0 0 24 24';
      break;
    default:
      svgpath = svgoutline;
      viewBox = '0 0 24 24';
  }
</script>

<svg xmlns="http://www.w3.org/2000/svg" role="button" tabindex="0" width={size} height={size} class={$$props.class} {...$$restProps} aria-label={ariaLabel} {viewBox} stroke-width="2" on:click>
  {@html svgpath}
</svg>

<!--
@component
[Go to docs](https://flowbite-svelte.com/)
## Props
@prop export let size: $$Props['size'] = '24';
@prop export let color: $$Props['color'] = 'currentColor';
@prop export let variation: $$Props['variation'] = 'outline';
@prop export let ariaLabel: $$Props['ariaLabel'] = 'bars 3';
-->
