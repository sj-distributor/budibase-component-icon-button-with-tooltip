<script>
  import { getContext } from "svelte";

  export let icon;
  export let iconColor;
  export let iconSize;
  export let onClick;
  export let canTooltip;
  export let tooltipText;

  const { styleable } = getContext("sdk");
  const component = getContext("component");

  const handleIconClick = () => {
    if (onClick) {
      onClick();
    }
  };

  const IconSizeOptions = {
    XXS: "ri-xxs",
    XS: "ri-xs",
    Small: "ri-sm",
    Medium: "ri-1x",
    Large: "ri-lg",
    XL: "ri-xl",
    "2XL": "ri-2x",
    "3XL": "ri-3x",
    "4XL": "ri-4x",
    "5XL": "ri-5x",
    "6XL": "ri-6x",
    "7XL": "ri-7x",
    "8XL": "ri-8x",
    "9XL": "ri-9x",
    "10XL": "ri-10x",
  };
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<div on:click={handleIconClick} use:styleable={$component.styles}>
  <i
    style="color:{iconColor}"
    class="{icon} {IconSizeOptions[iconSize]} svelte-1ghy1wa icon-container"
  >
    {#if !!canTooltip && !!tooltipText}
      <div class="tooltip">
        <div class="tooltip-content">
          <div class="tooltip-arrow">
            <span class="tooltip-arrow-content" />
          </div>

          <div class="tooltip-inner">
            <span>{tooltipText}</span>
          </div>
        </div>
      </div>
    {/if}
  </i>
</div>

<style>
  .icon-container {
    position: relative;
  }

  .icon-container:hover .tooltip-content {
    visibility: visible;
  }

  .tooltip {
    left: -12px;
    padding-top: 12px;
    visibility: hidden;
    position: absolute;
    transform-origin: 0px -4px;
  }

  .tooltip-content {
    margin: 0;
    padding: 0;
    z-index: 1070;
    display: block;
    font-size: 14px;
    max-width: 250px;
    list-style: none;
    position: absolute;
    box-sizing: border-box;
    color: rgba(0, 0, 0, 0.88);
    line-height: 1.5714285714285714;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
      "Helvetica Neue", Arial, "Noto Sans", sans-serif, "Apple Color Emoji",
      "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
  }

  .tooltip-arrow {
    top: 1px;
    left: 6px;
    z-index: 1;
    right: 6px;
    width: 32px;
    height: 32px;
    display: block;
    overflow: hidden;
    position: absolute;
    pointer-events: none;
    border-radius: 0 0 2px;
    box-sizing: border-box;
    transform: translateY(-100%);
  }

  .tooltip-arrow::before {
    bottom: 0;
    width: 32px;
    height: 8px;
    content: "";
    position: absolute;
    inset-inline-start: 0;
    box-sizing: border-box;
    background: rgba(0, 0, 0, 0.85);
    clip-path: path(
      "M 6.343145750507619 8 A 4 4 0 0 0 9.17157287525381 6.82842712474619 L 14.585786437626904 1.414213562373095 A 2 2 0 0 1 17.414213562373096 1.414213562373095 L 22.82842712474619 6.82842712474619 A 4 4 0 0 0 25.65685424949238 8 Z"
    );
  }

  .tooltip-arrow::after {
    bottom: 0;
    z-index: 0;
    content: "";
    margin: auto;
    inset-inline: 0;
    position: absolute;
    background: transparent;
    border-radius: 0 0 2px 0;
    width: 11.31370849898476px;
    height: 11.31370849898476px;
    transform: translateY(50%) rotate(-135deg);
    box-shadow: 3px 3px 7px rgb(0 0 0 / 10%);
  }

  .tooltip-arrow-content {
    pointer-events: none;
    box-sizing: border-box;
  }

  .tooltip-inner {
    color: #fff;
    min-width: 32px;
    min-height: 32px;
    padding: 6px 8px;
    text-align: start;
    border-radius: 6px;
    text-decoration: none;
    word-wrap: break-word;
    background-color: rgba(0, 0, 0, 0.85);
    box-shadow: 0 6px 16px 0 rgb(0 0 0 / 8%), 0 3px 6px -4px rgb(0 0 0 / 12%),
      0 9px 28px 8px rgb(0 0 0 / 5%);
  }
</style>
