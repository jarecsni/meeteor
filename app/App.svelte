<page>
    <actionBar title="Meeteor3" />
    <stackLayout>
        <label class="header" margin=10>Your Groups</label>
         <stackLayout orientation="horizontal" height="100">
            {#each myGroups as group}
                <dockLayout backgroundColor="lightgray" margin=10>
                    <label 
                        class="groupThumbnail"  
                        textWrap={true}
                        width=100
                    >
                        {group.name}
                    </label>
                </dockLayout>
            {/each}
         </stackLayout>
    </stackLayout>
</page>

<script>
    const myGroups = [
        {
            name: 'Sunday Book Club'
        },
        {
            name: 'Svelte Native Hackers'
        },
        {
            name: 'Svelte Stars'
        }
    ];
</script>

<style>
    .header {
        font-size: 24px;
    }
    .groupThumbnail {
        background-color: aqua;
    }
</style>

