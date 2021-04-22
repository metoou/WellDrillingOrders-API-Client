<template>
  <div class="customer-list">
    <div class="data">
      <table class="ui celled table">
        <thead>
          <tr>
            <th>Заказчик</th>
            <th>Подрядчик</th>
            <th>Месторождение</th>
            <th>№ скважины</th>
            <th>Назначение скважины</th>
            <th>Буровая установка</th>
            <th>Диаметр экс. колонны</th>
            <th>Глубина искусств. забоя</th>
            <th style="width: 170x;"></th>
          </tr>
        </thead>

        <tbody>
          <WellDrillingOrder
            v-for="wellDrillingOrder in wellDrillingOrders"
            :key="wellDrillingOrder.id"
            :wellDrillingOrder="wellDrillingOrder"
            @onDelete="onDelete"
            @onEdit="onEdit"
            @onShow="onShow"
          />
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import WellDrillingOrder from "./WellDrillingOrder";
export default {
  name: "WellDrillingOrderList",
  components: {
    WellDrillingOrder
  },
  props: {
    wellDrillingOrders: {
      type: Array
    }
  },
  methods: {
    onDelete(id) {
      // window.console.log("customer list delete " + id);
      this.$emit("onDelete", id);
    },
    onEdit(data) {
      // window.console.log("customer list edit " + data);
      this.$emit("onEdit", data);
    },
     onShow(data) {
      // window.console.log("customer list edit " + data);
      this.$emit("onShow", data);
    }
  }
};
</script>

<style scoped></style>
