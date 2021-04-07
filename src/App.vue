<template>
  <div id="app">
    <div class="app-title">
      <br>
      Доходы/Расходы <br>
      Итог: {{finalSumm}}
      <button @click="add =! add" class="button-add"><img src="./assets/add-512.png" height="25px" width="25px"/></button>
    </div>
    <div class="app-add" v-if="add">
      Имя: <input v-model="name" placeholder=""/><br>
      Сумма:<input v-model="income" placeholder="знак '-' если < 0"/><br>
      Дата:<input v-model="date" placeholder=""/><br>
      Тип:
      <select v-model="type">
        <option disabled value="">Выберите один из вариантов</option>
        <option>Доход</option>
        <option>Расход</option>
      </select>
      Описание:<textarea v-model="incomeDescription" placeholder=""/><br>
      <button @click="comm1(),add =! add, final()" id="removeAddButton"><img src="./assets/Unknown.png" height="25px" width="25px"/></button>
    </div>
    <div :class="{appAdd: isActive0, appAdd1: isPassive0}" v-if="add1">
      <button @click="edit =! edit , number(0)"><img src="./assets/edit.png" height="25px" width="25px"/></button>
      <button @click="add1 =! add1, removee(0), final()"><img src="./assets/delete.png" height="25px" width="25px"/></button> <br>
      Имя: {{this.addArray[0].name}} <br>
      Сумма: {{this.addArray[0].income}}<br>
      Дата: {{this.addArray[0].date}}<br>
      Тип: {{this.addArray[0].type}}<br>
      Описание: {{this.addArray[0].incomeDescription}}
    </div>
    <div :class="{appAdd: isActive1, appAdd1: isPassive1}" v-if="add2">
      <button @click="edit =! edit , number(1)"><img src="./assets/edit.png" height="25px" width="25px"/></button>
      <button @click="add2 =! add2, removee(1), final()"><img src="./assets/delete.png" height="25px" width="25px"/></button> <br>
      Имя: {{this.addArray[1].name}} <br>
      Сумма: {{this.addArray[1].income}}<br>
      Дата: {{this.addArray[1].date}}<br>
      Тип: {{this.addArray[1].type}}<br>
      Описание: {{this.addArray[1].incomeDescription}}
    </div>
    <div :class="{appAdd: isActive2, appAdd1: isPassive2}" v-if="add3">
      <button @click="edit =! edit , number(2)"><img src="./assets/edit.png" height="25px" width="25px"/></button>
      <button @click="add3 =! add3, removee(2), final()"><img src="./assets/delete.png" height="25px" width="25px"/></button> <br>
      Имя: {{this.addArray[2].name}} <br>
      Сумма: {{this.addArray[2].income}}<br>
      Дата: {{this.addArray[2].date}}<br>
      Тип: {{this.addArray[2].type}}<br>
      Описание: {{this.addArray[2].incomeDescription}}
    </div>
    <div :class="{appAdd: isActive3, appAdd1: isPassive3}" v-if="add4">
      <button @click="edit =! edit , number(3)"><img src="./assets/edit.png" height="25px" width="25px"/></button>
      <button @click="add4 =! add4, removee(3), final()"><img src="./assets/delete.png" height="25px" width="25px"/></button> <br>
      Имя: {{this.addArray[3].name}} <br>
      Сумма: {{this.addArray[3].income}}<br>
      Дата: {{this.addArray[3].date}}<br>
      Тип: {{this.addArray[3].type}}<br>
      Описание: {{this.addArray[3].incomeDescription}}
    </div>
    <div :class="{appAdd: isActive4, appAdd1: isPassive4}" v-if="add5">
      <button @click="edit =! edit , number(4)"><img src="./assets/edit.png" height="25px" width="25px"/></button>
      <button @click="add5 =! add5, removee(4), final()"><img src="./assets/delete.png" height="25px" width="25px"/></button> <br>
      Имя: {{this.addArray[4].name}} <br>
      Сумма: {{this.addArray[4].income}}<br>
      Дата: {{this.addArray[4].date}}<br>
      Тип: {{this.addArray[4].type}}<br>
      Описание: {{this.addArray[4].incomeDescription}}
    </div>
    <div :class="{appAdd: isActive5, appAdd1: isPassive5}" v-if="add6">
      <button @click="edit =! edit , number(5)"><img src="./assets/edit.png" height="25px" width="25px"/></button>
      <button @click="add6 =! add6, removee(5), final()"><img src="./assets/delete.png" height="25px" width="25px"/></button> <br>
      Имя: {{this.addArray[5].name}} <br>
      Сумма: {{this.addArray[5].income}}<br>
      Дата: {{this.addArray[5].date}}<br>
      Тип: {{this.addArray[5].type}}<br>
      Описание: {{this.addArray[5].incomeDescription}}
    </div>
    <div class="app-edit" v-if="edit">
      <p align="center">Редактирование элемента </p>
      Имя: <input v-model="name" placeholder="" /><br>
      Сумма:<input v-model="income" placeholder=""/><br>
      Дата:<input v-model="date" placeholder=""/><br>
      Описание:<textarea v-model="incomeDescription" placeholder=""/><br>
      <button @click="edits(), edit =! edit, final()"><img src="./assets/Unknown.png" height="25px" width="25px"/></button>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      finalSumm: 0,
      isActive0: '',
      isPassive0: '',
      isActive1: '',
      isPassive1: '',
      isActive2: '',
      isPassive2: '',
      isActive3: '',
      isPassive3: '',
      isActive4: '',
      isPassive4: '',
      isActive5: '',
      isPassive5: '',
      edit: false,
      edit2: false,
      edit3: false,
      edit4: false,
      edit5: false,
      edit6: false,
      add: false,
      add1: false,
      add2: false,
      add3: false,
      add4: false,
      add5: false,
      add6: false,
      name: '',
      income: '',
      date: '',
      type: '',
      incomeDescription: '',
      addArray: [],
      i: 0,
      addDiv: '',
      addDivB: ''
    }
  },
  methods: {
    final () {
      let r = 0
      for (let x = 0; x <= this.addArray.length; x++) {
        r = r + Number(this.addArray[x].income)
        this.finalSumm = r
      }
    },
    comm2 () {
      this.isActive = false
      this.isPassive = false
    },
    comm1 () {
      this.addArray.push({
        name: this.name,
        income: this.income,
        date: this.date,
        type: this.type,
        incomeDescription: this.incomeDescription
      })
      if (this.addArray[this.i].type === 'Доход') {
        switch (this.i) {
          case 0: this.isActive0 = true
            break
          case 1: this.isActive1 = true
            break
          case 2: this.isActive2 = true
            break
          case 3: this.isActive3 = true
            break
          case 4: this.isActive4 = true
            break
          case 5: this.isActive5 = true
            break
        }
      } else {
        switch (this.i) {
          case 0: this.isPassive0 = true
            break
          case 1: this.isPassive1 = true
            break
          case 2: this.isPassive2 = true
            break
          case 3: this.isPassive3 = true
            break
          case 4: this.isPassive4 = true
            break
          case 5: this.isPassive5 = true
            break
        }
      }
      switch (this.i) {
        case 0: this.add1 = true
          break
        case 1: this.add2 = true
          break
        case 2: this.add3 = true
          break
        case 3: this.add4 = true
          break
        case 4: this.add5 = true
          break
        case 5: this.add6 = true
          break
      }
      this.name = ''
      this.income = ''
      this.date = ''
      this.type = ''
      this.incomeDescription = ''
      this.i++
    },

    edits () {
      switch (this.n) {
        case 0:
          this.addArray[this.n].name = this.name
          this.addArray[this.n].income = this.income
          this.addArray[this.n].date = this.date
          this.addArray[this.n].incomeDescription = this.incomeDescription
          break
        case 1:
          this.addArray[this.n].name = this.name
          this.addArray[this.n].income = this.income
          this.addArray[this.n].date = this.date
          this.addArray[this.n].incomeDescription = this.incomeDescription
          break
        case 2:
          this.addArray[this.n].name = this.name
          this.addArray[this.n].income = this.income
          this.addArray[this.n].date = this.date
          this.addArray[this.n].incomeDescription = this.incomeDescription
          break
        case 3:
          this.addArray[this.n].name = this.name
          this.addArray[this.n].income = this.income
          this.addArray[this.n].date = this.date
          this.addArray[this.n].incomeDescription = this.incomeDescription
          break
        case 4:
          this.addArray[this.n].name = this.name
          this.addArray[this.n].income = this.income
          this.addArray[this.n].date = this.date
          this.addArray[this.n].incomeDescription = this.incomeDescription
          break
        case 5:
          this.addArray[this.n].name = this.name
          this.addArray[this.n].income = this.income
          this.addArray[this.n].date = this.date
          this.addArray[this.n].incomeDescription = this.incomeDescription
          break
        case 6:
          this.addArray[this.n].name = this.name
          this.addArray[this.n].income = this.income
          this.addArray[this.n].date = this.date
          this.addArray[this.n].incomeDescription = this.incomeDescription
          break
      }
    },
    removee (n) {
      switch (n) {
        case 0: this.addArray.splice(0, 1)
          break
        case 1: this.addArray.splice(1, 1)
          break
        case 2: this.addArray.splice(2, 1)
          break
        case 3: this.addArray.splice(3, 1)
          break
        case 4: this.addArray.splice(4, 1)
          break
        case 5: this.addArray.splice(5, 1)
          break
      }
      console.log(this.addArray)
    },
    number (a) {
      this.n = a
    }
  }
}
</script>

<style lang="scss">

#removeAddButton{
}

#app {
  margin-top: 150px;
  display: flex;
  flex-direction: column;
  align-items: center;

  .app-title {
    width: 300px;
    height: 100px;
    font-size: 25px;
    background-color: #5E92F7;
    text-align: center;
    border-radius: 10px;
  }
  .app-add{
    width: 300px;
    height: 200px;
    font-size: 25px;
    background-color: #F7DC5E;
    border-radius: 5px;
  }
  .app-div{
    width: 300px;
    height: 200px;
    font-size: 25px;
    background-color: #2bb7e2;
    border-radius: 10px;
  }
  .app-edit{
    width: 300px;
    height: 300px;
    font-size: 25px;
    background-color: #ED5AD1;
    border-radius: 10px;
  }
  .appAdd{
    width: 300px;
    height: 200px;
    font-size: 25px;
    background-color: #60E07A;
    border-radius: 10px;
  }
  .appAdd1{
    width: 300px;
    height: 200px;
    font-size: 25px;
    background-color: #F64325;
    border-radius: 10px;
  }
}
</style>
