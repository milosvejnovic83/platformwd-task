<template>
  <div id="quantityInput">
    <div id="minus">
        <select id="select" v-on:change="selected" v-model="quantityValue">
            <option v-for="(quantity, index) in quantities" v-bind:key="index" >{{ quantity.value }}</option>
        </select>
    </div>
    <div id="plus">
        <input id="input" type="number"><br>
        <button id="update" v-on:click="update">Update</button>
    </div>
  </div>
</template>

<script>
export default {
    name: 'QuantityInput',
    data() {
        return{       
        quantities: [
                { value: '0' },
                { value: '1' },
                { value: '2' },
                { value: '3' },
                { value: '4' },
                { value: '5' },
                { value: '6' },
                { value: '7' },
                { value: '8' },
                { value: '9' },
                { value: '10+' }
            ],
        quantityValue: ''
        }
        
    },
    props: {
        parentData: Object
    },
    methods: {
        selected: function () {
            var e = document.getElementById("select");
            var quantitySelected = e.options[e.selectedIndex].text;
            if(quantitySelected == '10+') {
                document.getElementById("minus").style.display = "none";
                document.getElementById("plus").style.display = "block";
            }     
            if(quantitySelected != '0' && quantitySelected != '10+') {
               this.$emit("inputData", this.quantityValue);
            }
            if(quantitySelected == '0') {
               alert("Quantity must be more then 0!!!")
            }         
            
        },
        update: function () {
            var selectedmin = this.parentData.selectedmin;
            var selectedmax = this.parentData.selectedmax;
            var quantityEntered = document.getElementById("input").value;
            if(quantityEntered >= selectedmin && quantityEntered <= selectedmax) {
                this.$emit("inputData", quantityEntered);
            } else if (quantityEntered < selectedmin) {
                alert("Quantity must be more then 0!!!")
            } else if (quantityEntered > selectedmax) {
                alert("Quantity must be less then 100!!!")
            }
        }
    }	
}
</script>

<style>
#select {
    width: 50px;
    height: 25px;
}
#input {
    margin-bottom: 5px;
    width: 66px;
    height: 19px;
    border: 2px solid #e7e7e7;
    border-radius: 3px;
}
#update {
    width: 70px;
    height: 25px;
    background-color: white;
    border: 2px solid #e7e7e7;
    border-radius: 3px;
}
#minus {
    display: block;
}
#plus {
    display: none;
}
</style>