<script>
  export let isActive = false;
  export let isFirst = false;
  export let isHover = false;
  export let getOptionLabel = undefined;
  export let item = undefined;
  export let filterText = '';

  let itemClasses = '';

  $: {
    const classes = [];
    if (isActive) { classes.push('active'); }
    if (isFirst) { classes.push('first'); }
    if (isHover) { classes.push('hover'); }
    if (item.isGroupHeader) { classes.push('groupHeader'); }
    if (item.isGroupItem) { classes.push('groupItem'); }
    itemClasses = classes.join(' ');
  }
</script>

<div class="item {itemClasses}">
  {@html getOptionLabel(item, filterText)}
</div>
