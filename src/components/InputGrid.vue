<template>
    <div class="componenet-wrapper">
      
        <div class="buttons-wrapper">
            <button @click="resetTable()">
                Reset
            </button>
        </div>
        <div class="grid-wrapper">
            <div class="grid-vertical">
                <div class="reps-title">
                    <p>Reps</p>
                </div>
                <div class="grid-horizontal">
                    <div class="rpe-title">
                        <p>R</p>
                        <p>P</p>
                        <p>E</p>
                    </div>
                    <div class="grid" @click="toggleCells($event)">
                        <div :key="'row' + j" class="row" v-for="j in width">
                            <div class="col" :key="'col' + n" v-for="n in height">
                                <Cell @enter="changeToSpan(this.curActive)" :n="n" :j="j" :grid="grid" :rpe="rpe" :multVal="multVal"/>
                            </div>
                        </div>
                    </div>
                    
                </div>
            </div>
        </div>
     
    
    </div>
</template>

<script>
import Cell from './Cell.vue';

export default {
    data() {
        return{
            height: 9,
            width: 13,
           grid: [
            100.0,
            97.8,
            95.5,
            93.9,
            92.2,
            90.7,
            89.2,
            87.8,
            86.3,
            85.0,
            83.7,
            82.4,
            81.1,
            79.9,
            78.6,
            77.4,
            76.2,
            75.1,
            73.9,
            72.3,
            70.7,
            69.4,
            68.0,
            66.7,
            65.3,
            64.0,
            62.6,
            61.3,
            59.9,
            58.6,
           ],
           rpe: [
            [10],
            [9.5],
            [9],
            [8.5],
            [8],
            [7.5],
            [7],
            [6.5],
           ],
            activeCell: false,
            curActive: HTMLElement = null,
            storedPercent: undefined,
            weights: false,
            multVal: null,
           
            
        }
        
    },
    components: {
        Cell
    },
    methods: {
        // onClick(){
        //     if(this.activeCell){
        //         let activePercent = this.curActive.id;
                
        //     }
        // }
        toggleCells(e){
            if(!e.target.id){
                this.changeToSpan(this.curActive);
                this.curActive = null;
                return;
            }
            console.log(this.curActive)
            if(this.curActive != null && this.curActive.nodeName === "INPUT" && e.target.nodeName === "INPUT")
                return;
            else if(this.curActive != null)
                this.changeToSpan(this.curActive);

            if(e.target.nodeName === "SPAN")
                this.changeToInput(e.target);
            else if (e.target.nodeName === "INPUT")
                this.changeToSpan(e.target);

        },
        changeToInput(elt){
            const sibling = elt.parentElement.nextSibling
            elt.style.display = "none";
            sibling.style.display = "inline"

            this.storedPercent = this.extractFloat(elt.id);
            this.curActive = sibling;
        },
        changeToSpan(elt){
            console.log(typeof(elt))
            const curVal = this.extractFloat(elt.value);
            console.log(curVal, this.storedPercent)
            if(curVal != this.storedPercent){
                this.weights = true;
                
                this.multVal = (curVal / this.storedPercent) * 100;
            }
            let sibling = elt.previousSibling.children[0];

            elt.style.display = "none";
            sibling.style.display = "inline"
        },
        extractFloat(string){
            return parseFloat(string.match(/-?(?:\d+(?:\.\d*)?|\.\d+)/))
        },
        resetTable(){
            this.multVal = null;
        }
    }
}
</script>


<style scoped>

input{
    max-width: 3rem;
    min-height: 2rem;
}
.grid-wrapper{
    display: flex;
    flex-direction: row;
}
.grid-vertical{
    display: flex;
    flex-direction: column;
}
.reps-title{
    margin: auto;
    padding: 0.5rem;
    font-size: 2rem;
}
.grid-horizontal{
    display: flex;
    flex-direction: row;
}
.rpe-title{
    margin: auto;
    padding: 1rem;
    font-size: 1.5rem;
}
.grid{
    border-radius: 0.25rem;

    display: flex;
    flex-direction: row;
}
.row{

}
.col{

}
.cell{
    padding: 0.5rem;
    border: 0.5px solid black;
}
</style>