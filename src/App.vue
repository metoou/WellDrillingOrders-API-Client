<template>
  <div id="app">
    <div class="ui fixed inverted menu vue-color">
      <div class="ui container">
        <a href="#" class="header item">Смета скважин</a>
      </div>
    </div>

    <div class="ui main container">
      <b-button id="show-btn" @click="onAdd()">Добавить новый наряд</b-button>
      <WellDrillingOrderList
        :wellDrillingOrders="wellDrillingOrders"
        @onDelete="onDelete"
        @onEdit="onEdit"
        @onShow="onShow"
      />
      <AddModalForm :form="form" @onFormSubmit="onFormSubmit" />
      <EditModalForm :form="form" @onFormSubmit="onFormSubmit" />
      <ShowModalForm :form="form" @onFormSubmit="onFormSubmit" />
      <Loader v-if="loader" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import AddModalForm from "./components/AddModalForm";
import EditModalForm from "./components/EditModalForm";
import ShowModalForm from "./components/ShowModalForm";
import WellDrillingOrderList from "./components/WellDrillingOrderList";
import Loader from "./components/Loader";

export default {
  name: "App",
  components: {
    AddModalForm,
    EditModalForm,
    ShowModalForm,
    WellDrillingOrderList,
    Loader
  },
  data() {
    return {
      url: "http://laravel.loc/api/wellDrillingOrders",
      wellDrillingOrders: [],
      form: { 
        form: { 
              customer: "", 
              contractor: "", 
              oilField: "", 
              wellNumber: "", 
              wellPurpose: "", 
              drillingRig: "", 
              wellDesign: "",
              direction: "", 
              conductor: "", 
              operatingColumn: "", 
              diameter: "", 
              artificialFaceDepth: "", 
              oilFinstallationDepthield: "", 
              isEdit: false 
            } },
      loader: false
    };
  },
  methods: {
    getWellDrillingOrders() {
      this.loader = true;

      axios.get(this.url).then(data => {
        this.wellDrillingOrders = data.data;
        this.loader = false;
      });
    },
    deleteWellDrillingOrder(id) {
      this.loader = true;

      axios
        .delete(`${this.url}/${id}`)
        .then(() => {
          this.getWellDrillingOrders();
        })
        .catch(e => {
          alert(e);
        });
    },
    createWellDrillingOrder(data) {
      this.loader = true;

      axios
        .post(this.url, {
          customer: data.customer,
          contractor: data.contractor,
          oilField: data.oilField,
          wellNumber: data.wellNumber,
          wellPurpose: data.wellPurpose,
          drillingRig: data.drillingRig,
          wellDesign: data.wellDesign,
          direction: data.direction,
          conductor: data.conductor,
          operatingColumn: data.operatingColumn,
          diameter: data.diameter,
          artificialFaceDepth: data.artificialFaceDepth,
          installationDepth: data.installationDepth,
        })
        .then(() => {
          this.getWellDrillingOrders();
        })
        .catch(e => {
          alert(e);
        });
    },
    editWellDrillingOrder(data) {
      this.loader = true;

      axios
        .put(`${this.url}/${data.id}`, {
          customer: data.customer,
          contractor: data.contractor,
          oilField: data.oilField,
          wellNumber: data.wellNumber,
          wellPurpose: data.wellPurpose,
          drillingRig: data.drillingRig,
          wellDesign: data.wellDesign,
          direction: data.direction,
          conductor: data.conductor,
          operatingColumn: data.operatingColumn,
          diameter: data.diameter,
          artificialFaceDepth: data.artificialFaceDepth,
          installationDepth: data.installationDepth,
        })
        .then(() => {
          this.getWellDrillingOrders();
        })
        .catch(e => {
          alert(e);
        });
    },
    onDelete(id) {
      // window.console.log("app delete " + id);
      this.deleteWellDrillingOrder(id);
    },
    onEdit(data) {
      // window.console.log("app edit ", data);
      this.$bvModal.show("bv-modal-wellDrillingOrderEdit");
      this.form = data;
      this.form.isEdit = true;
      this.getWellDrillingOrders();
    },
    onShow(data) {
      // window.console.log("app edit ", data);
      this.$bvModal.show("bv-modal-wellDrillingOrderShow");
      this.form = data;
    },
    onFormSubmit(data) {
      // window.console.log("app onFormSubmit", data);

      if (data.isEdit) {
        // call edit customer
        this.editWellDrillingOrder(data);
      } else {
        // call create customer
        this.createWellDrillingOrder(data);
      }
    },
    onAdd: function () {
      this.form.customer = "";
      this.form.contractor = "";
      this.form.oilField = "";
      this.form.wellNumber = "";
      this.form.wellPurpose = "";
      this.form.drillingRig = "";
      this.form.wellDesign = "";
      this.form.direction = "";
      this.form.conductor = "";
      this.form.operatingColumn = "";
      this.form.diameter = "";
      this.form.artificialFaceDepth = "";
      this.form.installationDepth = "";
      this.$bvModal.show("bv-modal-wellDrillingOrderAdd");
    },
  },
  created() {
    this.getWellDrillingOrders();
  }
};
</script>

<style>
.vue-color {
  background: #a0a5aa !important;
}

.main.container {
  margin-top: 60px;
}

.submit-button {
  margin-top: 24px !important;
  float: right;
}

.data {
  margin-top: 15px;
}

thead tr th {
  background: #e0e0e0 !important;
}

.ui.inverted.dimmer {
  background-color: rgba(255, 255, 255, 0) !important;
}
</style>
