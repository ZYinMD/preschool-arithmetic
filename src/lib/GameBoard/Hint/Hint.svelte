<script lang="ts">
  import { settings, showingHint } from '../../GameSettings/$settings';
  import Tiles from './Tiles.svelte';
  function handleClickHintButton() {
    if ($settings.allowHint === 'onClick') {
      $showingHint = true;
    }
  }
</script>

<div class="container">
  {#if $showingHint}
    <Tiles />
  {/if}

  {#if $settings.allowHint !== 'no'}
    <div class="button">
      <button on:click={handleClickHintButton}> 提示 </button>
    </div>
  {/if}
</div>

<style>
  .container {
    grid-area: hint;
    display: grid;
    grid:
      'tiles' auto
      'button' 3vw
      /
      auto;
  }
  .button {
    grid-area: button;
    display: grid;
    place-items: center;
  }
  button {
    font-size: 1.4vw;
    border: none;
    padding: 0.4vw 0.8vw 0.3vw;
    color: #aaa;
    background-color: transparent;
  }
</style>
