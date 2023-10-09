<script>
    import { FeedbackStore } from "../stores";
    import Card from "./Card.svelte";
    export let item;

    const handleItemDelete = (itemId) => {
        FeedbackStore.update((value) => value.filter((fb) => fb.id !== itemId));
    }
</script>

<Card>
    <div class="num-display">
        {item.rating}
    </div>
    <button class="close" on:click={() => handleItemDelete(item.id)}>
        X
    </button>
    <div class="text-display">
        {item.text}
    </div>
</Card>

<style>
    .num-display {
        position:absolute;
        top: -10px;
        left: -10px;
        width: 50px;
        height: 50px;
        background-color: #ff6a95;
        color: #fff;
        border: 1px #eee solid;
        border-radius: 50%;
        padding: 10px;
        text-align: center;
        font-size: 19px;
    }

    .close {
        position: absolute;
        top: 10px;
        right: 20px;
        cursor: pointer;
        border: none;
        background-color: transparent;
    }
</style>

