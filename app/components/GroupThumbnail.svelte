<stackLayout class="groupPanel">
    <image 
        src={thumbnail}
        class="groupThumbnail"
    />
    <label 
        class="groupLabel"  
        textWrap={true}
    >
        {name}
    </label>
    <!-- <button 
        class="leaveGroupButton" 
        on:tap={handleLeaveGroup}
    >
        Leave
    </button> -->
</stackLayout>

<script>
	export let name, thumbnail, handleLeaveGroup;
</script>

<style>
    .groupPanel {
        background-color: lightgray; 
        margin: 4;
    }
    .groupThumbnail {
        width: 100;
    }
    .groupLabel {
        margin-left: 4;
        width: 100;
        height: 50;
    }
</style>