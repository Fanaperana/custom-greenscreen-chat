<template>
    <div id="textBubble" ref="keyid" class="">
        {{message}}
    </div>
</template>
<script>
import { ref } from 'vue';

const keyid = ref(null);

export default {
    props: {
        message: String,
        keyid: Number
    },
    data: () => ({
        content: '',
        show: 1
    }),
    mounted () {
        this.hide(this.$refs.keyid);
    },
    methods: {
        hide (el) {
            if (typeof(el) !== undefined || el !== null) {
                el.style.opacity = 0;
                setTimeout(() => {
                    el.style.opacity = 1;
                }, 0);
                setTimeout(() => {
                    el.style.opacity = -0.1;
                    el.style.marginLeft = '20px';
                }, 6000);

                setTimeout(() => {
                    el.remove();
                }, 8000);
            } else {
                this.el.destroy();
            }  
        }
    }
}
</script>
<style scoped>
    #textBubble {
        -webkit-hyphens: auto;
        -moz-hyphens: auto;
        -ms-hyphens: auto;
        hyphens: auto;
        max-width: 100%;
        word-break: break-word;
        margin-bottom: 12px;
        line-height: 24px;
        background-color: #e6e5ea;
        color: black;
        padding: 5px 15px;
        border-radius: 10px;
        position: relative;
        margin-right:auto;
        /* opacity: 1; */
        transition: opacity .5s ease, margin .5s ease-out;
    }

    #textBubble:not(:last-child) {
        overflow: hidden;
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