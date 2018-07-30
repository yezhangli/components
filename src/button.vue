<template>
    <button class="g-button" :class="{[`icon-${iconPositon}`]:true}">
        <g-icon v-if="icon" :name="icon"></g-icon>
        <g-icon class="loading" name="loading"></g-icon>
        <div class="content">
            <slot></slot>
        </div>
    </button>
</template>
<script>
    export default{
        props:{
            icon:{},
            iconPositon:{
                type:String,
                default:'left',
                validator(value){
                    //return !(value !== 'left' && value !== 'right');
                    return value === 'left' || value === 'right'
                }
            }
        }
    }
</script>
<style lang="scss">
    @keyframes spin {
        0%{transform: rotate(0deg);}
        100%{transform: rotate(360deg);}
    }
    .g-button{
        font-size:var(--font-size);
        height:var(--button-height);
        padding:0 1em;
        border-radius: var(--border-radius);
        border:1px solid var( --border-color);
        background: var(--button-bg);
        display: inline-flex;
        align-items: center;
        justify-content: center;
        vertical-align: top;
        &:hover{
            border-color:var(--border-color-hover) ;
        }
        &:active{
            background-color: var(--button-active-bg);
        }
        &:focus{
            outline:none;
        }
        >.content{
            order:2;
        }
        >.g-icon{
            order:1;
            margin-right:.3em;
        }
        &.icon-right{
            >.content{
                order:1;
            }
            >.g-icon{
                order:2;
                margin-right:0;
                margin-left: .3em;
            }
        }
        .loading{
            animation: spin 3s infinite linear;
        }
    }

</style>