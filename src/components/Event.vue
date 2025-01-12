<template>
    <div class="event" :class="{show : true }">
        <p>{{ text }}</p>
        <button>닫기</button>
    </div>
</template>
<script>
export default {
    name: 'EventComponent',
    props: {
        text: String,
        isEventOpen: Boolean,
    },
    data(){
        return {
            isOpen : false,
        }
    }
}
</script>
<style>
    .event {
        background: #444;
        color: #fff;
        padding: 10px 20px;
        text-align: center;
        font-size: small;
    }

    .show{
        display: flex;
    }
    .event p {
        margin: 0;
    }

    .event button{
        margin: 0;
    }
</style>