<script lang="ts">

import FeedbackForm from "./components/FeedbackForm.svelte";
import FeedbackList from "./components/FeedbackList.svelte";
import FeedbackStats from "./components/FeedbackStats.svelte"

let feedback = [
	{
		id: 1,
		rating: 10,
		text: 'lorem ipsum adflak'
	}, 
	{
		id: 2,
		rating: 10,
		text: 'lorem ipsum adflak'
	},
	{
		id: 3,
		rating: 10,
		text: 'lorem ipsum adflak'
	},
	{
		id: 4,
		rating: 10,
		text: 'lorem ipsum adflak'
	}
]

$: count = feedback.length
$: average = feedback.reduce((a, {rating}) => a + rating, 0) / feedback.length
const deleteFeedback = (e) => {
	const itemId = e.detail

	feedback = feedback.filter((item) => item.id != itemId)
	
}

</script>

<main class="container">
	<FeedbackForm></FeedbackForm>
	<FeedbackStats {count} {average}/>
	<h1>{count}</h1>
	<h1>{average}</h1>
	<FeedbackList {feedback} on:delete-feedback=
	{deleteFeedback} />

</main>



