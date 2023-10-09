<script>
    import {createEventDispatcher} from "svelte";
    import {v4 as uuidv4} from 'uuid';
    import Button from "./Button.svelte";
    import Card from "./Card.svelte";
    import RatingSelect from "./RatingSelect.svelte";

    const dispatch = createEventDispatcher();
    const minTextThreshold = 10;
    let text = '';
    let message = null;
    let rating = 10;

    let btnDisabled = true;

    const handleInputText = () => {
        if (text.trim().length < minTextThreshold) {
            message = `Text must be at least ${minTextThreshold} characters long.`
            btnDisabled = true;
        } else {
            message = '';
            btnDisabled = false;
        }
    }

    const handleRatingSelected = e => rating = e.detail;

    const handleFormSubmit = () => {
        console.log("Form submitted");
        if (text.trim().length > minTextThreshold) {
            const newFeedback = {
                id: uuidv4(),
                text,
                rating: +rating,
            }
            dispatch('feedback-submit', newFeedback);
        }
    }
</script>

<Card>
    <header>
        <h2>How would you rate your service with us?</h2>
    </header>
    <form on:submit|preventDefault={handleFormSubmit}>
        <RatingSelect on:rating-select={handleRatingSelected} />
        <div class="input-group">
            <input type="text" bind:value={text} on:input={handleInputText} placeholder="Tell us something that keeps you coming back...">
            <Button  disabled={btnDisabled} type='submit'>Send</Button>
        </div>
        {#if message}
            <div class="message">{message}</div>
        {/if}
    </form>
</Card>

<style>
    header {
        max-width: 400px;
        margin: auto;
    }

    .input-group {
        display: flex;
        flex-direction: row;
        border: 1px #ccc solid;
        padding: 8px 10px;
        border-radius: 8px;
        margin-top: 15px;
    }

    input {
        flex-grow: 2;
        border: none;
        font-size: 16px;
    }

    input:focus {
        outline: none;
    }

    .message {
        padding-top: 10px;
        text-align: center;
        color: rebeccapurple;
    }
</style>