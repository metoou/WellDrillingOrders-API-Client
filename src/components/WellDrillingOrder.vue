<template>
  <tr>
    <td>{{ wellDrillingOrder.customer }}</td>
    <td>{{ wellDrillingOrder.contractor }}</td>
    <td>{{ wellDrillingOrder.oilField }}</td>
    <td>{{ wellDrillingOrder.wellNumber }}</td>
    <td>{{ wellDrillingOrder.wellPurpose }}</td>
    <td>{{ wellDrillingOrder.drillingRig }}</td>
    <td>{{ wellDrillingOrder.diameter }}</td>
    <td>{{ wellDrillingOrder.artificialFaceDepth }}</td>
    
    <td>
      <b-dropdown variant="primary">
      <template #button-content>
        <b-icon icon="gear-fill" aria-hidden="true"></b-icon> Действия
      </template>
      <b-dropdown-divider></b-dropdown-divider>
      <b-dropdown-item-button @click="onShow">Просмотр</b-dropdown-item-button>
      <b-dropdown-item-button @click="onEdit">Изменить</b-dropdown-item-button>
      <b-dropdown-divider></b-dropdown-divider>
      <b-dropdown-item-button variant="danger" @click="onDelete">
        <b-icon icon="trash-fill" aria-hidden="true"></b-icon>
        Удалить
      </b-dropdown-item-button>
    </b-dropdown>

      
      
    </td>
  </tr>
</template>

<script>
export default {
  name: "WellDrillingOrder",
  props: {
    wellDrillingOrder: {
      type: Object
    }
  },
  methods: {
    onDelete() {
      // window.console.log("customer delete " + this.customer.id);
      this.$emit("onDelete", this.wellDrillingOrder.id);
    },
    onEdit() {
      // window.console.log("customer edit " + this.customer.id);
      this.$emit("onEdit", this.wellDrillingOrder);
    },
    onShow() {
      // window.console.log("customer edit " + this.customer.id);
      this.$emit("onShow", this.wellDrillingOrder);
    }

  }
};
</script>

<style scoped></style>
