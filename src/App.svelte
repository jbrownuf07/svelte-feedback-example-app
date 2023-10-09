<script>
    import FeedbackForm from "./components/FeedbackForm.svelte";
	import FeedbackList from "./components/FeedbackList.svelte";
    import FeedbackStats from "./components/FeedbackStats.svelte";

	let feedback = [
		{
			id: 1,
			rating: 10,
			text: 'Qui proident quis ex deserunt enim veniam et incididunt laborum amet aliqua.'
		},
		{
			id: 2,
			rating: 8,
			text: 'Ex id id sunt consectetur consequat consectetur sit velit ullamco ex labore anim excepteur. In cillum id qui veniam aliqua voluptate magna ea velit veniam magna culpa amet. Incididunt est do cupidatat deserunt cillum magna labore aliquip. Labore quis reprehenderit et et dolore cupidatat quis tempor. Excepteur velit cillum mollit cupidatat est fugiat officia laboris. Aliqua non non mollit voluptate adipisicing proident consectetur sit est.'
		},
		{
			id: 3,
			rating: 9,
			text: 'Laboris officia qui laborum proident voluptate. Mollit duis veniam enim voluptate esse commodo voluptate proident aliqua voluptate commodo est voluptate elit. Culpa dolore aliqua quis velit. Voluptate aute enim id duis ut consequat qui tempor ad proident eu incididunt cillum duis. Laborum aute ea mollit est laboris quis. Commodo excepteur culpa amet eu. Non culpa magna cupidatat esse laboris est in.'
		},
	];

	const deleteFeedbackItem = (e) => {
		const itemId = e.detail;
		feedback = feedback.filter((fb) => fb.id !== itemId);
	}

	const addNewFeedback = (e) => {
		const newFeedback = e.detail;
		feedback = [newFeedback, ...feedback];
	}

	$: count = feedback.length;
	$: average = +feedback.reduce((acc, fb) => acc + fb.rating, 0) / count;
</script>

<main class='container'>
	<FeedbackForm on:feedback-submit={addNewFeedback} />
	<FeedbackStats {count} {average} />
	<FeedbackList {feedback} on:delete-feedback={deleteFeedbackItem} />
</main>
