<template>
  <div id="app">
   <div class="app-title-1">Доходы и Расходы
     <button @click="show =!show"><img src="./assets/add.png" height="30px" width="30px"></button>
   </div><br>
    <div class="app-title-2">Итог: {{total}}</div>
    <div class="add" v-show="show"><br>
      Название: <input v-model="name" placeholder="Название"/><br>
      Сумма: <input type="number" min="0" v-model="sum"  placeholder="Сумма"/><br>
      Дата:<input v-model="date" type="date" placeholder="Дата"/><br>
      Тип:
      <select required v-model="type">
        <option disabled value="">Выберите один из вариантов</option>
        <option>Доход</option>
        <option>Расход</option>
      </select> <br>
      Описание:<textarea v-model="description" placeholder=""/><br>
      <button @click="numberOfCard(),show =!show, array()"><img src="./assets/accept.png" height="30px" width="30px"></button>
  </div>
    <div :class="{income: classIncome1 , consumption: classConsumption1}" v-if="card1">
      <button style="margin-left: 230px" @click="edit1 =! edit1, rename(1), funcEditform(1)"><img src="./assets/edit.png" height="30px" width="40px"></button>
      <button @click="card1 = !card1, funcDelete(0), theTotal()"><img src="./assets/delete.png" height="30px" width="40px"></button><br>
      Название: {{this.data[0].name}}<br>
      Сумма: {{this.data[0].sum}} <br>
      Дата: {{this.data[0].date}} <br>
      Тип: {{this.data[0].type}} <br>
      Описание: {{this.data[0].description}}<br>
    </div>
    <div class="edit" v-if="edit1">
      <p align="center">Редактирование карточки:</p>
      <p align="center">{{name}}</p>
      Название: <input v-model="name" placeholder="name"/><br>
      Сумма: <input v-model="sum" type="number" min="0" placeholder="sum"/><br>
      Дата: <input v-model="date" type="date" placeholder="date"/><br>
      Тип:
      <select v-model="type" required>
        <option disabled value="">Выберите один из вариантов</option>
        <option>Доход</option>
        <option>Расход</option>
      </select> <br>
      Описание: <textarea v-model="description" placeholder="description"/><br>
      <button @click="edit1 =! edit1, funcEdit(1)"><img src="./assets/accept.png" height="30px" width="30px"></button>
    </div>

    <div :class="{income: classIncome2 , consumption: classConsumption2}" v-if="card2">
      <button style="margin-left: 230px" @click="edit2 =! edit2, rename(2), funcEditform(2)"><img src="./assets/edit.png" height="30px" width="40px"></button>
      <button @click="card2 = !card2, funcDelete(1), theTotal()"><img src="./assets/delete.png" height="30px" width="40px"></button><br>
      Название: {{this.data[1].name}}<br>
      Сумма: {{this.data[1].sum}} <br>
      Дата: {{this.data[1].date}} <br>
      Тип: {{this.data[1].type}} <br>
      Описание: {{this.data[1].description}}<br>
    </div>
    <div class="edit" v-if="edit2">
      <p align="center">Редактирование карточки:</p>
      <p align="center">{{name}}</p>
      Название: <input v-model="name" placeholder="name"/><br>
      Сумма: <input v-model="sum" type="number" min="0" placeholder="sum"/><br>
      Дата: <input v-model="date" type="date" placeholder="date"/><br>
      Тип:
      <select v-model="type" required>
        <option disabled value="">Выберите один из вариантов</option>
        <option>Доход</option>
        <option>Расход</option>
      </select><br>
      Описание: <textarea v-model="description" placeholder="description"/><br>
      <button @click="edit2 =! edit2, funcEdit(2)"><img src="./assets/accept.png" height="30px" width="30px"></button>
    </div>
    <div :class="{income: classIncome3 , consumption: classConsumption3}" v-if="card3">
      <button style="margin-left: 230px" @click="edit3 =! edit3, rename(3), funcEditform(3)"><img src="./assets/edit.png" height="30px" width="40px"></button>
      <button @click="card3 = !card3, funcDelete(2), theTotal()"><img src="./assets/delete.png" height="30px" width="40px"></button><br><br>
      Название: {{this.data[2].name}}<br>
      Сумма: {{this.data[2].sum}} <br>
      Дата: {{this.data[2].date}} <br>
      Тип: {{this.data[2].type}} <br>
      Описание: {{this.data[2].description}}<br>
    </div>
    <div class="edit" v-if="edit3">
      <p align="center">Редактирование карточки:</p>
      <p align="center">{{name}}</p>
      Название: <input v-model="name" placeholder="name"/><br>
      Сумма: <input v-model="sum" type="number" min="0" placeholder="sum"/><br>
      Дата: <input v-model="date" type="date" placeholder="date"/><br>
      Тип:
      <select v-model="type" required>
        <option disabled value="">Выберите один из вариантов</option>
        <option>Доход</option>
        <option>Расход</option>
      </select> <br>
      Описание: <textarea v-model="description" placeholder="description"/><br>
      <button @click="edit3 =! edit3, funcEdit(3)"><img src="./assets/accept.png" height="30px" width="30px"></button>
    </div>
    <div :class="{income: classIncome4 , consumption: classConsumption4}" v-if="card4">
      <button style="margin-left: 230px" @click="edit4 =! edit4, rename(4), funcEditform(4)"><img src="./assets/edit.png" height="30px" width="40px"></button>
      <button @click="card4 = !card4, funcDelete(3), theTotal()"><img src="./assets/delete.png" height="30px" width="40px"></button><br><br>
      Название: {{this.data[3].name}}<br>
      Сумма: {{this.data[3].sum}} <br>
      Дата: {{this.data[3].date}} <br>
      Тип: {{this.data[3].type}} <br>
      Описание: {{this.data[3].description}}<br>
    </div>
    <div class="edit" v-if="edit4">
      <p align="center">Редактирование карточки:</p>
      <p align="center">{{name}}</p>
      Название: <input v-model="name" placeholder="name"/><br>
      Сумма: <input v-model="sum" type="number" min="0" placeholder="sum"/><br>
      Дата: <input v-model="date" type="date" placeholder="date"/><br>
      Тип:
      <select v-model="type" required>
        <option disabled value="">Выберите один из вариантов</option>
        <option>Доход</option>
        <option>Расход</option>
      </select><br>
      Описание: <textarea v-model="description" placeholder="description"/><br>
      <button @click="edit4 =! edit4, funcEdit(4)"><img src="./assets/accept.png" height="30px" width="30px"></button>
    </div>
    <div :class="{income: classIncome5 , consumption: classConsumption5}" v-if="card5">
      <button style="margin-left: 230px" @click="edit5 =! edit5, rename(5), funcEditform(5)"><img src="./assets/edit.png" height="30px" width="40px"></button>
      <button @click="card5 = !card5, funcDelete(4), theTotal()"><img src="./assets/delete.png" height="30px" width="40px"></button><br><br>
      Название: {{this.data[4].name}}<br>
      Сумма: {{this.data[4].sum}} <br>
      Дата: {{this.data[4].date}} <br>
      Тип: {{this.data[4].type}} <br>
      Описание: {{this.data[4].description}}<br>
    </div>
    <div class="edit" v-if="edit5">
      <p align="center">Редактирование карточки:</p>
      <p align="center">{{name}}</p>
      Название: <input v-model="name" placeholder="name"/><br>
      Сумма: <input v-model="sum" type="number" min="0" placeholder="sum"/><br>
      Дата: <input v-model="date" type="date" placeholder="date"/><br>
      Тип:
      <select v-model="type" required>
        <option disabled value="">Выберите один из вариантов</option>
        <option>Доход</option>
        <option>Расход</option>
      </select><br>
      Описание: <textarea v-model="description" placeholder="description"/><br>
      <button @click="edit5 =! edit5, funcEdit(5)"><img src="./assets/accept.png" height="30px" width="30px"></button>
    </div>
    <div :class="{income: classIncome6 , consumption: classConsumption6}" v-if="card6">
      <button style="margin-left: 230px" @click="edit6 =! edit6, rename(6), funcEditform(6)"><img src="./assets/edit.png" height="30px" width="40px"></button>
      <button @click="card6 = !card6, funcDelete(5), theTotal()"><img src="./assets/delete.png" height="30px" width="40px"></button><br>
      Название: {{this.data[5].name}}<br>
      Сумма: {{this.data[5].sum}} <br>
      Дата: {{this.data[5].date}} <br>
      Тип: {{this.data[5].type}} <br>
      Описание: {{this.data[5].description}}<br>
    </div>
    <div class="edit" v-if="edit6">
      <p align="center">Редактирование карточки:</p>
      <p align="center">{{name}}</p>
      Название: <input v-model="name" placeholder="name"/><br>
      Сумма: <input v-model="sum" type="number" min="0" placeholder="sum"/><br>
      Дата: <input v-model="date" type="date" placeholder="date"/><br>
      Тип:
      <select v-model="type" required>
        <option disabled value="">Выберите один из вариантов</option>
        <option>Доход</option>
        <option>Расход</option>
      </select><br>
      Описание: <textarea v-model="description" placeholder="description"/><br>
      <button @click="edit6 =! edit6, funcEdit(6)"><img src="./assets/accept.png" height="30px" width="30px"></button>
    </div>
    <div :class="{income: classIncome7 , consumption: classConsumption7}" v-if="card6">
      <button style="margin-left: 230px" @click="edit7 =! edit7, rename(7),funcEditform(7)"><img src="./assets/edit.png" height="30px" width="40px"></button>
      <button @click="card6 = !card6, funcDelete(6), theTotal()"><img src="./assets/delete.png" height="30px" width="40px"></button><br>
      Название: {{this.data[6].name}}<br>
      Сумма: {{this.data[6].sum}} <br>
      Дата: {{this.data[6].date}} <br>
      Тип: {{this.data[6].type}} <br>
      Описание: {{this.data[6].description}}<br>
    </div>
    <div class="edit" v-if="edit7">
      <p align="center">Редактирование карточки:</p>
      <p align="center">{{name}}</p>
      Название: <input v-model="name" placeholder="name"/><br>
      Сумма: <input v-model="sum" type="number" min="0" placeholder="sum"/><br>
      Дата: <input v-model="date" type="date" placeholder="date"/><br>
      Тип:
      <select v-model="type" required>
        <option disabled value="">Выберите один из вариантов</option>
        <option>Доход</option>
        <option>Расход</option>
      </select><br>
      Описание: <textarea v-model="description" placeholder="description"/><br>
      <button @click="edit7 =! edit7, funcEdit(7)"><img src="./assets/accept.png" height="30px" width="30px"></button>
    </div>
    <div :class="{income: classIncome8 , consumption: classConsumption8}" v-if="card8">
      <button style="margin-left: 230px" @click="edit8 =! edit8, rename(8), funcEditform(8)"><img src="./assets/edit.png" height="30px" width="40px"></button>
      <button @click="card8 = !card8, funcDelete(7), theTotal()"><img src="./assets/delete.png" height="30px" width="40px"></button><br>
      Название: {{this.data[7].name}}<br>
      Сумма: {{this.data[7].sum}} <br>
      Дата: {{this.data[7].date}} <br>
      Тип: {{this.data[7].type}} <br>
      Описание: {{this.data[7].description}}<br>
    </div>
    <div class="edit" v-if="edit8">
      <p align="center">Редактирование карточки:</p>
      <p align="center">{{name}}</p>
      Название: <input v-model="name" placeholder="name"/><br>
      Сумма: <input v-model="sum" type="number" min="0" placeholder="sum"/><br>
      Дата: <input v-model="date" type="date" placeholder="date"/><br>
      Тип:
      <select v-model="type" required>
        <option disabled value="">Выберите один из вариантов</option>
        <option>Доход</option>
        <option>Расход</option>
      </select><br>
      Описание: <textarea v-model="description" placeholder="description"/><br>
      <button @click="edit8 =! edit8, funcEdit(8)"><img src="./assets/accept.png" height="30px" width="30px"></button>
    </div>
    <div :class="{income: classIncome9 , consumption: classConsumption9}" v-if="card9">
      <button style="margin-left: 230px" @click="edit9 =! edit9, rename(9), funcEditform(9)"><img src="./assets/edit.png" height="30px" width="40px"></button>
      <button @click="card9 = !card9, funcDelete(8), theTotal()"><img src="./assets/delete.png" height="30px" width="40px"></button><br>
      Название: {{this.data[8].name}}<br>
      Сумма: {{this.data[8].sum}} <br>
      Дата: {{this.data[8].date}} <br>
      Тип: {{this.data[8].type}} <br>
      Описание: {{this.data[8].description}}<br>
    </div>
    <div class="edit" v-if="edit9">
      <p align="center">Редактирование карточки:</p>
      <p align="center">{{name}}</p>
      Название: <input v-model="name" placeholder="name"/><br>
      Сумма: <input v-model="sum" type="number" min="0" placeholder="sum"/><br>
      Дата: <input v-model="date" type="date" placeholder="date"/><br>
      Тип:
      <select v-model="type" required>
        <option disabled value="">Выберите один из вариантов</option>
        <option>Доход</option>
        <option>Расход</option>
      </select><br>
      Описание: <textarea v-model="description" placeholder="description"/><br>
      <button @click="edit9 =! edit9, funcEdit(9)"><img src="./assets/accept.png" height="30px" width="30px"></button>
    </div>
    <div :class="{income: classIncome10 , consumption: classConsumption10}" v-if="card10">
      <button style="margin-left: 230px" @click="edit10 =! edit10, rename(10), funcEditform(10)"><img src="./assets/edit.png" height="30px" width="40px"></button>
      <button @click="card10 = !card10, funcDelete(9), theTotal()"><img src="./assets/delete.png" height="30px" width="40px"></button><br>
      Название: {{this.data[9].name}}<br>
      Сумма: {{this.data[9].sum}} <br>
      Дата: {{this.data[9].date}} <br>
      Тип: {{this.data[9].type}} <br>
      Описание: {{this.data[9].description}}<br>
    </div>
    <div class="edit" v-if="edit10">
      <p align="center">Редактирование карточки:</p>
      <p align="center">{{name}}</p>
      Название: <input v-model="name" placeholder="name"/><br>
      Сумма: <input v-model="sum" type="number" min="0" placeholder="sum"/><br>
      Дата: <input v-model="date" type="date" placeholder="date"/><br>
      Тип:
      <select v-model="type" required>
        <option disabled value="">Выберите один из вариантов</option>
        <option>Доход</option>
        <option>Расход</option>
      </select><br>
      Описание: <textarea v-model="description" placeholder="description"/><br>
      <button @click="edit10 =! edit10, funcEdit(10)"><img src="./assets/accept.png" height="30px" width="30px"></button>
    </div>
    </div>
</template>

<script>
export default {
  data () {
    return {
      total: 0,
      total1: 0,
      total2: 0,
      name: '',
      sum: '',
      date: '',
      type: '',
      description: '',
      data: [],
      i: 1,
      k: 0,
      show: false,
      card1: false,
      edit1: false,
      classIncome1: false,
      classConsumption1: false,
      card2: false,
      edit2: false,
      classIncome2: false,
      classConsumption2: false,
      card3: false,
      edit3: false,
      classIncome3: false,
      classConsumption3: false,
      card4: false,
      edit4: false,
      classIncome4: false,
      classConsumption4: false,
      card5: false,
      edit5: false,
      classIncome5: false,
      classConsumption5: false,
      card6: false,
      edit6: false,
      classIncome6: false,
      classConsumption6: false,
      card7: false,
      edit7: false,
      classIncome7: false,
      classConsumption7: false,
      card8: false,
      edit8: false,
      classIncome8: false,
      classConsumption8: false,
      card9: false,
      edit9: false,
      classIncome9: false,
      classConsumption9: false,
      card10: false,
      edit10: false,
      classIncome10: false,
      classConsumption10: false
    }
  },
  watch: {
    sum () {
      this.theTotal()
    }
  },
  methods: {
    funcDelete (i) {
      this.data[i].sum = 0
    },
    funcEditform (i) {
      switch (i) {
        case 1:
          this.edit2 = false
          this.edit3 = false
          this.edit4 = false
          this.edit5 = false
          this.edit6 = false
          this.edit7 = false
          this.edit8 = false
          this.edit9 = false
          this.edit10 = false
          break
        case 2:
          this.edit1 = false
          this.edit3 = false
          this.edit4 = false
          this.edit5 = false
          this.edit6 = false
          this.edit7 = false
          this.edit8 = false
          this.edit9 = false
          this.edit10 = false
          break
        case 3:
          this.edit1 = false
          this.edit2 = false
          this.edit4 = false
          this.edit5 = false
          this.edit6 = false
          this.edit7 = false
          this.edit8 = false
          this.edit9 = false
          this.edit10 = false
          break
        case 4:
          this.edit1 = false
          this.edit2 = false
          this.edit3 = false
          this.edit5 = false
          this.edit6 = false
          this.edit7 = false
          this.edit8 = false
          this.edit9 = false
          this.edit10 = false
          break
        case 5:
          this.edit1 = false
          this.edit2 = false
          this.edit3 = false
          this.edit4 = false
          this.edit6 = false
          this.edit7 = false
          this.edit8 = false
          this.edit9 = false
          this.edit10 = false
          break
        case 6:
          this.edit1 = false
          this.edit2 = false
          this.edit3 = false
          this.edit4 = false
          this.edit5 = false
          this.edit7 = false
          this.edit8 = false
          this.edit9 = false
          this.edit10 = false
          break
        case 7:
          this.edit1 = false
          this.edit2 = false
          this.edit3 = false
          this.edit4 = false
          this.edit5 = false
          this.edit6 = false
          this.edit8 = false
          this.edit9 = false
          this.edit10 = false
          break
        case 8:
          this.edit1 = false
          this.edit2 = false
          this.edit3 = false
          this.edit4 = false
          this.edit5 = false
          this.edit6 = false
          this.edit7 = false
          this.edit9 = false
          this.edit10 = false
          break
        case 9:
          this.edit1 = false
          this.edit2 = false
          this.edit3 = false
          this.edit4 = false
          this.edit5 = false
          this.edit6 = false
          this.edit7 = false
          this.edit8 = false
          this.edit10 = false
          break
        case 10:
          this.edit1 = false
          this.edit2 = false
          this.edit3 = false
          this.edit4 = false
          this.edit5 = false
          this.edit6 = false
          this.edit7 = false
          this.edit8 = false
          this.edit9 = false
          break
      }
    },
    theTotal () {
      let r = 0
      let x = 0
      for (let i = 0; i < this.data.length; i++) {
        if (this.data[i].type === 'Доход') {
          r = r + (Number(this.data[i].sum))
        } else {
          x = x + (Number(this.data[i].sum))
        }
      }
      this.total = r - x
    },
    numberOfCard () {
      switch (this.i) {
        case 1:
          this.card1 = true
          this.i++
          this.k++
          break
        case 2:
          this.card2 = true
          this.i++
          this.k++
          break
        case 3:
          this.card3 = true
          this.i++
          this.k++
          break
        case 4:
          this.card4 = true
          this.i++
          this.k++
          break
        case 5:
          this.card5 = true
          this.i++
          this.k++
          break
        case 6:
          this.card6 = true
          this.i++
          this.k++
          break
        case 7:
          this.card7 = true
          this.i++
          this.k++
          break
        case 8:
          this.card8 = true
          this.i++
          this.k++
          break
        case 9:
          this.card9 = true
          this.i++
          this.k++
          break
        case 10:
          this.card10 = true
          this.i++
          this.k++
          break
      }
    },
    array () {
      this.data.push({
        name: this.name,
        sum: this.sum,
        date: this.date,
        type: this.type,
        description: this.description
      })
      this.classCard()
      this.name = ''
      this.sum = ''
      this.date = ''
      this.type = ''
      this.description = ''
    },
    funcEdit (i) {
      switch (i) {
        case 1:
          this.data[0].name = this.name
          this.data[0].sum = this.sum
          this.data[0].date = this.date
          this.data[0].type = this.type
          this.data[0].description = this.description
          this.classCardEdit(1)
          this.name = ''
          this.sum = ''
          this.date = ''
          this.type = ''
          this.description = ''
          break
        case 2:
          this.data[1].name = this.name
          this.data[1].sum = this.sum
          this.data[1].date = this.date
          this.data[1].type = this.type
          this.data[1].description = this.description
          this.classCardEdit(2)
          this.name = ''
          this.sum = ''
          this.date = ''
          this.type = ''
          this.description = ''
          break
        case 3:
          this.data[2].name = this.name
          this.data[2].sum = this.sum
          this.data[2].date = this.date
          this.data[2].type = this.type
          this.data[2].description = this.description
          this.classCardEdit(3)
          this.name = ''
          this.sum = ''
          this.date = ''
          this.type = ''
          this.description = ''
          break
        case 4:
          this.data[3].name = this.name
          this.data[3].sum = this.sum
          this.data[3].date = this.date
          this.data[3].type = this.type
          this.data[3].description = this.description
          this.classCardEdit(4)
          this.name = ''
          this.sum = ''
          this.date = ''
          this.type = ''
          this.description = ''
          break
        case 5:
          this.data[4].name = this.name
          this.data[4].sum = this.sum
          this.data[4].date = this.date
          this.data[4].type = this.type
          this.data[4].description = this.description
          this.classCardEdit(5)
          this.name = ''
          this.sum = ''
          this.date = ''
          this.type = ''
          this.description = ''
          break
        case 6:
          this.data[5].name = this.name
          this.data[5].sum = this.sum
          this.data[5].date = this.date
          this.data[5].type = this.type
          this.data[5].description = this.description
          this.classCardEdit(6)
          this.name = ''
          this.sum = ''
          this.date = ''
          this.type = ''
          this.description = ''
          break
        case 7:
          this.data[6].name = this.name
          this.data[6].sum = this.sum
          this.data[6].date = this.date
          this.data[6].type = this.type
          this.data[6].description = this.description
          this.classCardEdit(7)
          this.name = ''
          this.sum = ''
          this.date = ''
          this.type = ''
          this.description = ''
          break
        case 8:
          this.data[7].name = this.name
          this.data[7].sum = this.sum
          this.data[7].date = this.date
          this.data[7].type = this.type
          this.data[7].description = this.description
          this.classCardEdit(8)
          this.name = ''
          this.sum = ''
          this.date = ''
          this.type = ''
          this.description = ''
          break
        case 9:
          this.data[8].name = this.name
          this.data[8].sum = this.sum
          this.data[8].date = this.date
          this.data[8].type = this.type
          this.data[8].description = this.description
          this.classCardEdit(9)
          this.name = ''
          this.sum = ''
          this.date = ''
          this.type = ''
          this.description = ''
          break
        case 10:
          this.data[9].name = this.name
          this.data[9].sum = this.sum
          this.data[9].date = this.date
          this.data[9].type = this.type
          this.data[9].description = this.description
          this.classCardEdit(10)
          this.name = ''
          this.sum = ''
          this.date = ''
          this.type = ''
          this.description = ''
          break
      }
    },
    rename (i) {
      switch (i) {
        case 1:
          this.name = this.data[0].name
          this.sum = this.data[0].sum
          this.date = this.data[0].date
          this.type = this.data[0].type
          this.description = this.data[0].description
          break
        case 2:
          this.name = this.data[1].name
          this.sum = this.data[1].sum
          this.date = this.data[1].date
          this.type = this.data[1].type
          this.description = this.data[1].description
          break
        case 3:
          this.name = this.data[2].name
          this.sum = this.data[2].sum
          this.date = this.data[2].date
          this.type = this.data[2].type
          this.description = this.data[2].description
          break
        case 4:
          this.name = this.data[3].name
          this.sum = this.data[3].sum
          this.date = this.data[3].date
          this.type = this.data[3].type
          this.description = this.data[3].description
          break
        case 5:
          this.name = this.data[4].name
          this.sum = this.data[4].sum
          this.date = this.data[4].date
          this.type = this.data[4].type
          this.description = this.data[4].description
          break
        case 6:
          this.name = this.data[5].name
          this.sum = this.data[5].sum
          this.date = this.data[5].date
          this.type = this.data[5].type
          this.description = this.data[5].description
          break
        case 7:
          this.name = this.data[6].name
          this.sum = this.data[6].sum
          this.date = this.data[6].date
          this.type = this.data[6].type
          this.description = this.data[6].description
          break
        case 8:
          this.name = this.data[7].name
          this.sum = this.data[7].sum
          this.date = this.data[7].date
          this.type = this.data[7].type
          this.description = this.data[7].description
          break
        case 9:
          this.name = this.data[8].name
          this.sum = this.data[8].sum
          this.date = this.data[8].date
          this.type = this.data[8].type
          this.description = this.data[8].description
          break
        case 10:
          this.name = this.data[9].name
          this.sum = this.data[9].sum
          this.date = this.data[9].date
          this.type = this.data[9].type
          this.description = this.data[9].description
          break
      }
    },
    classCard () {
      if (this.type === 'Доход') {
        switch (this.k) {
          case 1:
            this.classIncome1 = true
            this.classConsumption1 = false
            break
          case 2:
            this.classIncome2 = true
            this.classConsumption2 = false
            break
          case 3:
            this.classIncome3 = true
            this.classConsumption3 = false
            break
          case 4:
            this.classIncome4 = true
            this.classConsumption4 = false
            break
          case 5:
            this.classIncome5 = true
            this.classConsumption5 = false
            break
          case 6:
            this.classIncome6 = true
            this.classConsumption6 = false
            break
          case 7:
            this.classIncome7 = true
            this.classConsumption7 = false
            break
          case 8:
            this.classIncome8 = true
            this.classConsumption8 = false
            break
          case 9:
            this.classIncome9 = true
            this.classConsumption9 = false
            break
          case 10:
            this.classIncome10 = true
            this.classConsumption10 = false
            break
        }
      } else {
        switch (this.k) {
          case 1:
            this.classIncome1 = false
            this.classConsumption1 = true
            break
          case 2:
            this.classIncome2 = false
            this.classConsumption2 = true
            break
          case 3:
            this.classIncome3 = false
            this.classConsumption3 = true
            break
          case 4:
            this.classIncome4 = false
            this.classConsumption4 = true
            break
          case 5:
            this.classIncome5 = false
            this.classConsumption5 = true
            break
          case 6:
            this.classIncome6 = false
            this.classConsumption6 = true
            break
          case 7:
            this.classIncome7 = false
            this.classConsumption7 = true
            break
          case 8:
            this.classIncome8 = false
            this.classConsumption8 = true
            break
          case 9:
            this.classIncome9 = false
            this.classConsumption9 = true
            break
          case 10:
            this.classIncome10 = false
            this.classConsumption10 = true
            break
        }
      }
    },
    classCardEdit (i) {
      if (this.type === 'Доход') {
        switch (i) {
          case 1:
            this.classIncome1 = true
            this.classConsumption1 = false
            break
          case 2:
            this.classIncome2 = true
            this.classConsumption2 = false
            break
          case 3:
            this.classIncome3 = true
            this.classConsumption3 = false
            break
          case 4:
            this.classIncome4 = true
            this.classConsumption4 = false
            break
          case 5:
            this.classIncome5 = true
            this.classConsumption5 = false
            break
          case 6:
            this.classIncome6 = true
            this.classConsumption6 = false
            break
          case 7:
            this.classIncome7 = true
            this.classConsumption7 = false
            break
          case 8:
            this.classIncome8 = true
            this.classConsumption8 = false
            break
          case 9:
            this.classIncome9 = true
            this.classConsumption9 = false
            break
          case 10:
            this.classIncome10 = true
            this.classConsumption10 = false
            break
        }
      } else {
        switch (i) {
          case 1:
            this.classIncome1 = false
            this.classConsumption1 = true
            break
          case 2:
            this.classIncome2 = false
            this.classConsumption2 = true
            break
          case 3:
            this.classIncome3 = false
            this.classConsumption3 = true
            break
          case 4:
            this.classIncome4 = false
            this.classConsumption4 = true
            break
          case 5:
            this.classIncome5 = false
            this.classConsumption5 = true
            break
          case 6:
            this.classIncome6 = false
            this.classConsumption6 = true
            break
          case 7:
            this.classIncome7 = false
            this.classConsumption7 = true
            break
          case 8:
            this.classIncome8 = false
            this.classConsumption8 = true
            break
          case 9:
            this.classIncome9 = false
            this.classConsumption9 = true
            break
          case 10:
            this.classIncome10 = false
            this.classConsumption10 = true
            break
        }
      }
    }
  }
}
</script>
<style lang="scss">
#app {
  display: flex;
  flex-direction: column;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  align-items: center;
  color: #2c3e50;
  .app-title-1 {
    font-size: 36px;
  }
  .app-title-2 {
    font-size: 30px;
  }
  .add {
    height: 210px;
    width: 350px;
    background-color: #72A7FC;
    border-radius: 10px;
  }
  .income{
    background-color: #5CE68E;
    border-radius: 10px;
    height: 250px;
    width: 350px;
  }
  .edit {
    background-color: #A83FE0;
    border-radius: 10px;
    height: 270px;
    width: 350px;
  }
  .consumption {
    background-color: #FF5646;
    border-radius: 10px;
    height: 250px;
    width: 350px;
  }
}
</style>
