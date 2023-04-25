<script>
  import { getContext } from "svelte";

  export let icon;
  export let iconColor;
  export let iconSize;
  export let onClick;
  export let canTooltip;
  export let tooltipText;
  export let placement;

  const { styleable } = getContext("sdk");
  const component = getContext("component");

  const handleIconClick = () => {
    if (onClick) {
      onClick();
    }
  };
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<div
  class="container"
  on:click={handleIconClick}
  use:styleable={$component.styles}
>
  <span class="u-tooltip-showOnHover">
    <i
      style="color:{iconColor}"
      class="{icon} {iconSize} svelte-1ghy1wa icon-container"
    >
      {#if !!canTooltip && !!tooltipText}
        <span class="spectrum-Tooltip spectrum-Tooltip--{placement}">
          <span class="spectrum-Tooltip-label">{tooltipText}</span>
          <span class="spectrum-Tooltip-tip" />
        </span>
      {/if}
    </i>
  </span>
</div>

<style>
  .container {
    cursor: pointer;
  }

  .u-tooltip-showOnHover {
    z-index: 1070;
  }

  .icon-container:hover .spectrum-Tooltip.spectrum-Tooltip--top {
    transform: translate(
      -50%,
      calc(
        -1 * var(--spectrum-tooltip-tip-margin, var(--spectrum-global-dimension-size-150))
      )
    );
  }

  .spectrum-Tooltip {
    font-size: 14px;
    list-style: none;
    background: rgba(0, 0, 0, 0.85);
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
      "Helvetica Neue", Arial, "Noto Sans", sans-serif, "Apple Color Emoji",
      "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
  }

  .spectrum-Tooltip-tip {
    border-top-color: rgba(0, 0, 0, 0.85);
  }
</style>
