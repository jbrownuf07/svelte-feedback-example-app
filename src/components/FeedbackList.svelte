<script>
    import { FeedbackStore } from "../stores";
    import { fade, scale } from "svelte/transition";
    import FeedbackItem from "./FeedbackItem.svelte";
    export let feedback = [];

    FeedbackStore.subscribe((value) => feedback = value);
</script>

{#each feedback as fb (fb.id)}
    <div in:scale out:fade="{{ duration: 500 }}">
        <FeedbackItem item={fb} on:delete-feedback />
    </div>
{/each}