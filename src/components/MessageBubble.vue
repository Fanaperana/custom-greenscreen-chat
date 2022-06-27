<template>
    <div id="textBubble">
        {{message}}
    </div>
</template>
<script>
export default {
    props: ['message']
}
</script>
<style scoped>
    #textBubble {
        max-width: 300px;
        word-wrap: break-word;
        margin-bottom: 12px;
        line-height: 24px;
        background-color: #e6e5ea;
        color: black;
        padding: 10px 20px;
        border-radius: 20px;
        position: relative;
        margin-left:auto;
        margin-right:auto;
    }

    #textBubble::before,
    #textBubble::after {
        content: "";
        width: 25px;
        height: 25px;
        position: absolute;
        bottom: 0;
    }

    #textBubble::before {
		left: -7px;
        width: 20px;
        background-color: #E5E5EA;
		border-bottom-right-radius: 16px 14px;
	}

	#textBubble::after {
		left: -26px;
        width: 26px;
        background-color: #00B140;
		border-bottom-right-radius: 10px;
	}
</style>