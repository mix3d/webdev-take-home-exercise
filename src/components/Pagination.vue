<template>
    <div class="pagination">
        <svg viewBox="0 0 34 34">
            <path d="M16,0H0V16" transform="translate(10.4 17.014) rotate(-45)"/>
        </svg>
        <h2 class="pages">
            1/1
        </h2>
        <svg viewBox="0 0 34 34">
            <path d="M16,0H0V16" transform="translate(23.627 17.014) rotate(135)"/>
        </svg>

    </div>
</template>

<script>
// TODO: support pagination, with current/max page props and 
export default {

}
</script>

<style lang="scss">
.pagination{
    display: flex;
    padding: 0 1rem;
    margin-top: 1rem;
    align-items: center;
    justify-content: center;

    .pages{
        flex-grow:1;
        // display:flex;
        // align-items: center;
        text-align: center;
        letter-spacing: 1rem;
        max-width: 400px;
        //letter-spacing doesn't center right... magic numbers here!
        padding-left: 12px;
    }
    svg {
        width: 48px;
        height: 48px;

        border-radius: 50%;
        border: none;
        padding: 0.75rem;

        &:hover{
            color: var(--accent);
            box-shadow: var(--soft-shadow);
        }
        &:active{
            color: var(--theme);
        }
    }
    path{
        fill: none;
        stroke: currentColor;
        stroke-linecap: round;
        stroke-width: 4px;
    }
}
</style>
