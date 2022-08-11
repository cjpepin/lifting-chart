<template>
     <div class="cell">
        <div v-if="n === 1 && j === 1" style="color: white;"> .</div>
        <div v-else-if="j === 1">{{rpe[n-2][0]}}</div>
        <div v-else-if="n === 1">{{j-1}}</div>
        <div  v-else>
            <span ref="span" :id="grid[n + 2 * (j-1) -4]"> 
                <span v-if="multVal !== null" :id="grid[n + 2 * (j-1) -4]">
                    {{parseInt((grid[n + 2 * (j-1) -4] / 100 * multVal) * 100)/100}}
                </span>
                <span v-else :id="grid[n + 2 * (j-1) -4]">
                    {{grid[n + 2 * (j-1) -4]}}%
                </span>
            </span>
            <input ref="input" 
                    type="number" 
                    :id="'input-' + grid[n + 2 * (j-1) -4]" 
                    :value="grid[n + 2 * (j-1) -4]" 
                    style="display: none"
                    @keyup.enter="$emit('enter')"/>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return{
            activeCell: false,
            curActive: HTMLElement,
        }
        
    },
    props: ['n',
    'j',
    'grid',
    'rpe',
    'multVal'],
    methods: {
    }
        
}
</script>


<style scoped>
.cell{
    padding: 0.5rem;
    border: 0.5px solid black;
}
input{
    max-width: 3rem;
    min-height: 1rem;
}
</style>