<script>
    import FeedbackItem from "./FeedbackItem.svelte";
    export let feedback = [];
</script>

{#each feedback as fb (fb.id)}
    <div>
        <FeedbackItem item={fb} on:delete-feedback />
    </div>
{/each}