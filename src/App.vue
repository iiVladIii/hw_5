<template>
  <div id="app">
   <div class="app-title">
     <p> Доходы и Расходы
    <button @click="add =! add" class="button-add"><img src="./assets/add-512.png" height="25px" width="25px"/></button>
       <button @click="edit =! edit" class="button-add"><img src="./assets/add-512.png" height="25px" width="25px"/></button>
     </p>
     <p>Выручка:{{incomeValue - incomExpense}}</p>
     </div>
    <div class="edit" v-if="edit">
      Имя: <input v-model="newname" placeholder=""/><br>
      Сумма:<input v-model="money" placeholder=""/><br>
      Дата:<input v-model="date" placeholder=""/><br>
      Описание:<textarea v-model="incomeDescription" placeholder=""/><br>
      <button @click="editor()" class="button-add1"><img src="./assets/Unknown.png" height="20px" width="20px"/></button>
<!--      <button @click="delete1" class="button-add1"><img src="./assets/Unknown.png" height="20px" width="20px"/></button>-->
    </div>
    <div class="add" v-if="add">
      Имя: <input v-model="name" placeholder=""/><br>
      Сумма:<input v-model="income" placeholder=""/><br>
      Дата:<input v-model="date" placeholder=""/><br>
      Тип:
      <select v-model="selected">
      <option disabled value="">Выберите один из вариантов</option>
      <option>Доход</option>
      <option>Расход</option>
    </select>
      <span>Выбрано: {{ selected }}</span> <br>
      Описание:<textarea v-model="incomeDescription" placeholder=""/><br>
      <button @click="qwert()" class="button-add1"><img src="./assets/Unknown.png" height="25px" width="25px"/></button>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      edit: false,
      selected: '',
      date: '',
      type: '',
      name: '',
      income: '',
      incomeDescription: '',
      incomeValue: 0,
      add: false,
      arrays: [],
      i: -1,
      div: '',
      incomExpense: '',
      newname: '',
      money: ''
    }
  },
  methods: {
    qwert () {
      this.arrays.push({
        name: this.name,
        type: this.selected,
        income: this.income,
        date: this.date,
        incomeDescription: this.incomeDescription
      })
      if (this.selected === 'Доход') {
        this.i++
        this.incomeValue = this.incomeValue + Number(this.arrays[this.i].income)
        this.div = document.createElement('div')
        this.div.className = 'app-income'
        this.div.innerText =
          'Название: ' + this.arrays[this.i].name + '   ' +
        ' Тип: ' + this.arrays.[this.i].type + '   ' +
        ' Сумма: ' + this.arrays.[this.i].income + '   ' +
        ' Дата: ' + this.arrays.[this.i].date + '   ' +
        ' Описание: ' + this.arrays.[this.i].incomeDescription
        this.div.setAttribute('id', this.arrays.[this.i].name)
        document.querySelector('#app').append(this.div)
        // this.but = document.createElement('button')
        // this.but.className = 'button-xxxx'
        // this.but.setAttribute('id', 'x')
        // document.querySelector('#this.i').append(this.but)
      } else {
        this.i++
        this.incomExpense = this.incomExpense + Number(this.arrays[this.i].income)
        this.div = document.createElement('div')
        this.div.className = 'app-expense'
        this.div.innerText =
          'Название:' + this.arrays[this.i].name + '   ' +
          ' Тип: ' + this.arrays.[this.i].type + '   ' +
          ' Сумма: ' + this.arrays.[this.i].income + '   ' +
          ' Дата: ' + this.arrays.[this.i].date + '   ' +
          ' Описание: ' + this.arrays.[this.i].incomeDescription
        this.div.setAttribute('id', this.arrays.[this.i].name)
        document.querySelector('#app').append(this.div)
      }
    },
    editor () {
      for (let k = 0; k <= length.this.arrays; k++) {
        if (this.arrays[k].name === this.newname) {
          console.log(this.arrays[k].name)
          this.arrays[k].name = this.newname
          this.arrays[k].income = this.money
          this.arrays[k].date = this.date
          this.arrays[k].incomeDescription = this.incomeDescription
          this.div = document.getElementById('this.name')
          this.div.innerText =
            'Название: ' + this.arrays[this.k].name + '   ' +
            ' Тип: ' + this.arrays.[this.k].type + '   ' +
            ' Сумма: ' + this.arrays.[this.k].income + '   ' +
            ' Дата: ' + this.arrays.[this.k].date + '   ' +
           ' Описание: ' + this.arrays.[this.k].incomeDescription
        }
      }
    }
  }
}
</script>

<style lang="scss">
#app {
  margin-top: 200px;
  display: flex;
  flex-direction: column;
  align-items: center;
  .app-title{
    font-size: 25px;
    background-color: #E0B643;
  }
  .app-income{
    width:175px;
    font-size: 18px;
    background-color: #76F540;
    border: 3px double black;
  }

  .add {
    background-color: #2FD1DE;
    width:250px;
    font-size: 18px;
    border: 3px double black;
  }
}
.app-expense{
  background-color: #FF4E17;
  width:175px;
  font-size: 18px;
  border: 3px double black;
}
.button-add {
  float:bottom;

  }
.button-add1{
  margin-left: 105px;
}
.button-xxxx{
  margin-left: 150px;

}
.edit{
  background-color: #2FD1DE;
  width:250px;
  font-size: 18px;
  border: 3px double black;
}

</style>
