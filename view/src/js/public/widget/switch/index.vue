<script>
function s4 () {
    return Math.floor((1 + Math.random()) * 0x10000).toString(16).substring(1);
}

function uuid () {
    return s4() + s4() + '-' + s4() + '-' + s4() + '-' + s4() + '-' + s4() + s4() + s4();
}

export default {
    props : {
        checked : Boolean,
    },
    data () {
        return {
            id : `switch-${ uuid() }`,
            value : this.checked,
        };
    },
    methods : {
        change () {
            console.log('change', this.value);
            this.$emit('change', this.value);
        },
    },
    watch : {
        checked ( checked ) {
            this.value = checked;
        },
    },
};
</script>

<template>
    <div class="widget-switch">
        <label :for="id" class="switch-cell">
            <input :id="id" class="switch-cell-input" type="checkbox" v-model="value" @change="change">
            <div class="switch-cell-box"></div>
        </label>
    </div>
</template>

<style lang="scss" scoped>
    @import "./switch";
    .widget-switch {
        @include switch;
    }
</style>
