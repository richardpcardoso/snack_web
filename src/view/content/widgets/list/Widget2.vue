<template>
  <div class="card card-custom card-stretch gutter-b">
    <!--begin::Header-->
    <div class="card-header border-0 pt-5">
      <h3 class="card-title align-items-start flex-column">
        <span class="card-label font-weight-bolder text-dark"
          >Seus Produtos</span
        >
        <span class="text-muted mt-3 font-weight-bold font-size-sm"
          >Confira a baixo os seus produtos</span
        >
      </h3>
      <div class="card-toolbar">
        <router-link
          to="/novo/produto"
          v-slot="{ href, navigate, isActive, isExactActive }"
        >
          <a :href="href" class="btn btn-warning btn-sm" @click="navigate">
            <span class="menu-text"> Adicionar</span>
          </a>
        </router-link>
      </div>
    </div>
    <!--end::Header-->
    <!--begin::Body-->
    <div class="card-body pt-2 pb-0">
      <!--begin::Table-->
      <div class="table-responsive">
        <table class="table table-borderless table-vertical-center">
          <thead>
            <tr>
              <th class="p-0" style="width: 50px"></th>
              <th class="p-0" style="min-width: 150px"></th>
              <th class="p-0" style="min-width: 140px"></th>
              <th class="p-0" style="min-width: 120px"></th>
              <th class="p-0" style="min-width: 40px"></th>
            </tr>
          </thead>
          <tbody>
            <template v-for="(item, i) in dataToShow">
              <tr v-bind:key="i">
                <td class="pl-0 py-5">
                  <img
                      :src="`${item.img}`"
                      class="max-w-80px align-self-center rounded-lg"
                      alt=""
                  />
                </td>
                <td class="pl-0">
                  <a
                    href="#"
                    class="text-dark font-weight-bolder text-hover-primary mb-1 font-size-lg"
                    >{{ item.title }}</a
                  >
                  <span class="text-muted font-weight-bold d-block">{{
                    item.desc
                  }}</span>
                </td>
                <td class="text-right">
                  <span class="text-muted font-weight-bold">{{
                    item.desc2
                  }}</span>
                </td>
                <td class="text-right">
                  <span class="text-muted font-weight-bold">{{
                    item.users
                  }}</span>
                </td>
                <td class="text-right pr-0">
                  <a href="#" class="btn btn-icon btn-light btn-sm">
                    <span class="svg-icon svg-icon-md svg-icon-success">
                      <!--begin::Svg Icon | path:assets/media/svg/icons/Navigation/Arrow-right.svg-->
                      <inline-svg
                        src="media/svg/icons/Design/Edit.svg"
                      ></inline-svg>
                      <!--end::Svg Icon-->
                    </span>
                  </a>
                </td>
              </tr>
            </template>
          </tbody>
        </table>
      </div>
      <!--end::Table-->
    </div>
    <!--end::Body-->
  </div>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  name: "widget-12",
  data() {
    return {
      show: "day",
      day: [
        {
          title: "Popular Authors",
          desc: "Sem descrição",
          desc2: "Marmita",
          users: "Indisponível",
          img: "media/produtos/1.png"
        },
        {
          title: "Mister",
          desc: "Sem descrição",
          desc2: "Marmita",
          users: "Disponível",
          img: "media/produtos/2.png"
        },
        {
          title: "Select",
          desc: "Sem descrição",
          desc2: "Marmita",
          users: "Disponível",
          img: "media/produtos/3.png"
        },
        {
          title: "Palácio",
          desc: "Sem descrição",
          desc2: "Marmita",
          users: "Disponível",
          img: "media/produtos/4.png"
        },
        {
          title: "Point",
          desc: "Sem descrição",
          desc2: "Marmita",
          users: "Disponível",
          img: "media/produtos/5.png"
        },
        {
          title: "Arte",
          desc: "Sem descrição",
          desc2: "Marmita",
          users: "Disponível",
          img: "media/produtos/6.png"
        },
        {
          title: "Go",
          desc: "Sem descrição",
          desc2: "Marmita",
          users: "Disponível",
          img: "media/produtos/7.png"
        }
      ]
    };
  },
  computed: {
    ...mapGetters(["layoutConfig"]),
    dataToShow() {
      if (this.show === "month") return this.month;
      if (this.show === "week") return this.week;
      if (this.show === "day") return this.day;
      return this.day;
    }
  }
};
</script>
