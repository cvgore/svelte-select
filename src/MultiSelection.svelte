<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  export let selectedValue = [];
  export let activeSelectedValue = undefined;
  export let isDisabled = false;
  export let multiFullItemClearable = false;
  export let getSelectionLabel = undefined;

  function handleClear(i, event) {
    event.stopPropagation();
    dispatch('multiItemClear', {i});
  }
</script>

{#each selectedValue as value, i}
<div class="multiSelectItem {activeSelectedValue === i ? 'active' : ''} {isDisabled ? 'disabled' : ''}" on:click={event => multiFullItemClearable ? handleClear(i, event) : {}}>
  <div class="multiSelectItem_label">
    {@html getSelectionLabel(value)}
  </div>
  {#if !isDisabled && !multiFullItemClearable}
  <div class="multiSelectItem_clear" on:click="{event => handleClear(i, event)}">
    <svg width="100%" height="100%" viewBox="-2 -2 50 50" focusable="false" role="presentation">
      <path
        d="M34.923,37.251L24,26.328L13.077,37.251L9.436,33.61l10.923-10.923L9.436,11.765l3.641-3.641L24,19.047L34.923,8.124 l3.641,3.641L27.641,22.688L38.564,33.61L34.923,37.251z"></path>
    </svg>
  </div>
  {/if}
</div>
{/each}
