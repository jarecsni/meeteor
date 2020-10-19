<BottomNavigation>
    <actionBar title="Svelte Native App" />
    <tabs>
        <tabStrip>
            <tabStripItem title="Explorer" />
            <tabStripItem title="Home" />
            <tabStripItem title="Alerts" />
        </tabStrip>
    </tabs>
</BottomNavigation>

<script>
    import { BottomNavigation } from 'svelte-native/components'
    let message = "Blank Svelte Native App"
</script>

<style>
    .info .fas {
        color: #3A53FF;
    }
    .info {
        font-size: 20;
    }
</style>
