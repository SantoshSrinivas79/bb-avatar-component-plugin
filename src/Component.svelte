<script>
  import { getContext } from "svelte"

  export let imageUrl
  export let size
  export let title
  export let caption 
  export let isShowingDetails

  const { styleable } = getContext("sdk")
  const component = getContext("component")
</script>

<div use:styleable={$component.styles}>
  <div class="container">
    <div style="flex: 0 0 auto;">
      <img src="{imageUrl}" alt="avatar" class="image-class" style="--size:{size}"/>
    </div>
    {#if isShowingDetails}
    <div class="text-container">
      <span>{title}</span>
      <p class="caption">{caption}</p>
    </div>
    {/if}
  </div>
</div>

<style>
.container {
  display: flex;
  align-items: center;
}

.image-class {
  border-radius: 50%;
  height: var(--size, 32px);
  width: var(--size, 32px);
  object-fit: cover;
  overflow: hidden;
}

.text-container {
  color: black;
  font-size: 12px;
  font-weight: 600;
  line-height: 16px;
  overflow-wrap: break-word;
  margin-left: 8px;
  overflow: hidden;
  text-overflow: ellipsis;  
  white-space: nowrap;
}

.caption {
  font-weight: 400;
}
</style>