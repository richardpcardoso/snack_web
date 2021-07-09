<template>
  <!--begin::Aside Secondary-->
  <div
    class="sidebar sidebar-left d-flex flex-row-auto flex-column"
    id="kt_sidebar"
    ref="kt_sidebar"
  >
    <!--begin::Aside Secondary Header-->
    <div
      class="sidebar-header flex-column-auto pt-5 pt-lg-19 pb-5 px-5 px-lg-10"
    >
      <!--begin::Toolbar-->
      <div class="d-flex justify-content-between align-items-center pr-2 mb-6">

        <span class="text-muted font-weight-bold font-size-lg flex-grow-1">
          <h3 class="text-dark font-weight-bolder line-height-lg">Olá, Yuri</h3>
          FoodBox
        </span>
        <img
            :src="`media/empresas/Group5.png`"
            class="max-w-125px align-self-center"
            alt=""
        />
      </div>
      <!--end::Toolbar-->
    </div>
    <!--end::Aside Secondary Header-->
    <!--begin::Aside Secondary Content-->
    <div class="sidebar-content flex-column-fluid pb-10 pt-9 px-5 px-lg-10">
      <!--begin: Stats Widget 19-->
      <div class="card card-custom bg-warning card-shadowless gutter-b">
        <!--begin::Body-->
        <div class="card-body my-3">
          <a
            href="#"
            class="card-title font-weight-bolder text-white text-hover-state-white font-size-h6 mb-4 d-block"
            >Entregas para Hoje</a>
          <div class="font-weight-bold text-white font-size-sm">
            <span class="text-white font-size-h2 font-weight-bolder mr-2">26</span>
            Pedidos
          </div>
        </div>
        <!--end:: Body-->
      </div>
      <!--end: Stats:Widget 19-->
      <!--begin::Stats Widget 20-->
      <div class="card card-custom bg-white card-shadowless gutter-b">
        <!--begin::Body-->
        <div class="card-body my-4">
          <a
            href="#"
            class="card-title font-weight-bolder text-warning font-size-h6 mb-4 text-hover-state-dark d-block"
            >Entregas agendas</a
          >
          <div class="font-weight-bold text-warning font-size-sm">
            <span class="text-warning font-weight-bolder font-size-h2 mr-2"
              >87</span
            >Pedidos
          </div>
        </div>
        <!--end::Body-->
      </div>
<!--      <ListWidget1></ListWidget1>-->
    </div>
    <!--end::Aside Secondary Content-->
  </div>
  <!--end::Aside Secondary-->
</template>

<style lang="scss">
/* hide default vue-bootstrap tab links */
.hide-tabs > div:not(.tab-content) {
  display: none;
}
</style>

<script>
import KTLayoutSidebar from "@/assets/js/layout/base/sidebar.js";
import ListWidget1 from "@/view/content/widgets/list/Widget1.vue";

export default {
  name: "sidebar",
  components: {
    ListWidget1
  },
  mounted() {
    this.$nextTick(() => {
      // Init sidebar
      KTLayoutSidebar.init(this.$refs["kt_sidebar"]);
    });
  }
};
</script>
