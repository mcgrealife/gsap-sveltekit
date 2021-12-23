<script>
    
    export let m
    export let d
    
    let innerWindowWidth
    $: mobile = innerWindowWidth <= 900
    
    $: padding = mobile ? m + "px" : d + "px"
    
    
    </script>
    
    <svelte:window bind:innerWidth={innerWindowWidth} />
    
    <div style="height:{padding}">
        
    </div>
    
    
    
    