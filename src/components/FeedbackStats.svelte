<script>
    import { FeedbackStore } from "../stores";
    let feedback = [];
    FeedbackStore.subscribe((value) => feedback = value);

	$: count = feedback.length;
	$: average = (+feedback.reduce((acc, fb) => acc + fb.rating, 0) / count).toFixed(1);
</script>

<div class="feedback-stats">
    <h4>{count} Reviews</h4>
    <h4>Ratings Average: {average}</h4>
</div>

<style>
   .feedback-stats {
        display: flex;
        justify-content: space-between;
        align-items: center;
    } 
</style>