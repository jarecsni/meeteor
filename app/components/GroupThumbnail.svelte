<stackLayout backgroundColor="lightgray" margin=4>
    <image 
        src={thumbnail}
        width="100"
        height="100"
        top=0
    />
    <label 
        class="groupThumbnail"  
        textWrap={true}
        width=90
        height=50
        top=40
        marginLeft=4
    >
        {name}
    </label>
    <button height=20 on:tap={handleLeaveGroup}>Leave</button>
</stackLayout>

<script>
	export let name, thumbnail, handleLeaveGroup;
</script>

<style>
    .groupThumbnail {
        opacity: 1;
    }
</style>