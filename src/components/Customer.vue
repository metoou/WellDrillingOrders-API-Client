<template>
<div>
 <tr>
    <td>Заказчик</td>
    <td>{{ customer.customer }}</td>
 </tr>
  <tr>
    <td>Подрядчик </td>
    <td>{{ customer.contractor }}</td>
 </tr>
  <tr>
    <td>Месторождение </td>
    <td>{{ customer.oilField }}</td>
 </tr>
  <tr>
    <td>Номер скважины</td>
    <td>{{ customer.wellNumber }}</td>
 </tr>
  <tr>
    <td>Назначение скважины</td>
    <td>{{ customer.wellPurpose }}</td>
 </tr>
  <tr>
    <td>Буровая установка</td>
    <td>{{ customer.drillingRig }}</td>
 </tr>
  <tr>
    <td>Конструкция скважины</td>
    <td>{{ customer.wellDesign }}</td>
 </tr>
  <tr>
    <td>Направление </td>
    <td>{{ customer.direction }}</td>
 </tr>
  <tr>
    <td>Кондуктор </td>
    <td>{{ customer.conductor }}</td>
 </tr>
 <tr>
    <td>Эксплутационная колонна </td>
    <td>{{ customer.operatingColumn }}</td>
 </tr>
 <tr>
    <td>Диаметр  </td>
    <td>{{ customer.diameter }}</td>
 </tr>
 <tr>
    <td>Глубина искусственного забоя </td>
    <td>{{ customer.artificialFaceDepth }}</td>
 </tr>
 <tr>
    <td>Глубина установки </td>
    <td>{{ customer.installationDepth }}</td>
 </tr>

 <tr>
   <td></td>
    <td>
      <button class="mini ui blue button" @click="onEdit">Изменить</button>
      <button class="mini ui red button" @click="onDelete">Удалить</button>
    </td>
  </tr>
</div>
</template>

<script>
export default {
  name: "Customer",
  props: {
    customer: {
      type: Object
    }
  },
  methods: {
    onDelete() {
      // window.console.log("customer delete " + this.customer.id);
      this.$emit("onDelete", this.customer.id);
    },
    onEdit() {
      // window.console.log("customer edit " + this.customer.id);
      this.$emit("onEdit", this.customer);
    }
  }
};
</script>

<style>
.ui.table {
  border: none;
}
.ui.container {
  width: 1300px!important;
}
.ui.table tbody{
  border: none;
  display: flex;
  flex-wrap: wrap;
}
.ui.table div{
  margin-right: 20px;
  margin-bottom: 20px;
}
.ui.celled.table tr td {
  width: 50%;
}
.ui.celled.table tr td:first-child {
  border-left: 1px solid rgba(34,36,38,.15);
}
.ui.celled.table tr td:last-child {
  border-right: 1px solid rgba(34,36,38,.15);
  
}
.ui.table tr:first-child td {
    border-top: 1px solid rgba(34,36,38,.15);
}
.ui.table tr:last-child td {
    border-bottom: 1px solid rgba(34,36,38,.15);
}
</style>
