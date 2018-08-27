<template>
    <button class="g-button" :class="{[`icon-${iconPosition}`]:true}" @click="$emit('click')">
        <g-icon class="loading icon" v-if="loading" name="loading"></g-icon>
        <g-icon v-if="icon && !loading" class="icon" :name="icon"></g-icon>
        <div class="content">
            <slot></slot>
        </div>
    </button>
</template>
<script>
import Icon from './icon'
    export default{
        components:{
            'g-icon':Icon
        },
        props:{
            icon:{},
            loading:{
                type:Boolean,
                default:false
            },
            iconPosition:{
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
<<<<<<< HEAD
=======
        display: inline-flex;
        align-items: center;
        justify-content: center;
        vertical-align: top;
>>>>>>> 2830ff27693a3c2d678dec2318a7c82790215909
        &:hover{
            border-color:var(--border-color-hover) ;
        }
        &:active{
            background-color: var(--button-active-bg);
        }
        &:focus{
            outline:none;
        }
<<<<<<< HEAD
=======
        >.content{
            order:2;
        }
        >.icon{
            order:1;
            margin-right:.3em;
        }
        &.icon-right{
            >.content{
                order:1;
            }
            >.icon{
                order:2;
                margin-right:0;
                margin-left: .3em;
            }
        }
        .loading{
            animation: spin 3s infinite linear;
        }
>>>>>>> 2830ff27693a3c2d678dec2318a7c82790215909
    }

</style>