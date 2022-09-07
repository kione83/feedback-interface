<script>
	import FeedbackForm from "./components/FeedbackForm.svelte";
	import FeedbackList from "./components/FeedbackList.svelte";
	import FeedbackStats from "./components/FeedbackStats.svelte";

	let ratings = [
		{ id: "1", rating: 9, text: "This is a great product" },
		{
			id: "2",
			rating: 8,
			text: "This is a good product, but it had a few issues",
		},
		{
			id: "3",
			rating: 9,
			text: `This was a great product, but it's not perfect. I would like to see more features in the future`,
		},
		{
			id: "4",
			rating: 10,
			text: `This is a fantastic product, and I would recommend it to anyone`,
		},
	];
	$: count = ratings.length;
	$: average =
		ratings.reduce((acc, { rating }) => acc + rating, 0) / ratings.length;
	const deleteFeedback = (e) => {
		const itemId = e.detail;
		ratings = ratings.filter((item) => item.id != itemId);
	};

	const addFeedback = (e) => {
		const newFeedback = e.detail;
		ratings = [newFeedback, ...ratings];
	};
</script>

<main class="container">
	<FeedbackForm on:add-feedback={addFeedback} />
	<FeedbackStats {count} {average} />
	<FeedbackList feedback={ratings} on:delete-feedback={deleteFeedback} />
</main>

<style>
</style>
