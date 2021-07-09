<template>
  <div>
    <div class="row mt-0 mt-lg-20">
      <div class="col-xl-12 px-10 mb-20">
        <div class="card card-custom bgi-no-repeat gutter-b" style="height: 200px; background-color: #FCEDD4; background-position: calc(100% + 10rem) 100%; background-size: 60% auto; background-image: url(/media/svg/patterns/taieri.svg)">
          <!--begin::Body-->
          <div class="card-body d-flex align-items-center">
            <img
                :src="`media/misc/delivery.png`"
                class="max-w-300px align-self-center"
                alt=""
            />
            <div class="ml-10">
              <h3 class="text-warning font-weight-bolder line-height-lg mb-5">Olá, Yuri</h3>
              <a href="#" class="btn btn-sm btn-warning font-weight-bold px-6 py-3">Vizualizar entregar de hoje</a>
            </div>
          </div>
          <!--end::Body-->
        </div>
      </div>
    </div>

    <div class="row">
      <div class="col-md-12 px-10">
        <KTCodePreview v-bind:title="'Calendario de Pedidos'">
          <template v-slot:preview>
            <p>
              Neste calendario possui suas vendas durante o dia.
            </p>
            <v-row>
              <v-col>
                <v-sheet height="400">
                  <v-calendar
                      ref="calendar"
                      :now="code1.today"
                      :value="code1.today"
                      :events="code1.events"
                      color="primary"
                      type="week"
                  ></v-calendar>
                </v-sheet>
              </v-col>
            </v-row>
          </template>
          <template v-slot:html>
            {{ code1.html }}
          </template>
          <template v-slot:js>
            {{ code1.js }}
          </template>
        </KTCodePreview>
      </div>
    </div>
  </div>
</template>

<script>
import KTCodePreview from "@/view/content/CodePreview.vue";
import { SET_BREADCRUMB } from "@/core/services/store/breadcrumbs.module";

export default {
  name: "dashboard",
  components: {
    KTCodePreview
  },
  mounted() {
    this.$store.dispatch(SET_BREADCRUMB, [{ title: "Dashboard" }]);
  },
  data() {
    return {
      code1: {
        html: `<v-row>
  <v-col>
    <v-sheet height="400">
      <v-calendar
        ref="calendar"
        :now="today"
        :value="today"
        :events="events"
        color="primary"
        type="week"
      ></v-calendar>
    </v-sheet>
  </v-col>
</v-row>`,
        js: ` export default {
    data: () => ({
      today: '2020-01-08',
      events: [
        {
          name: 'Weekly Meeting',
          start: '2020-01-07 09:00',
          end: '2020-01-07 10:00',
        },
        {
          name: 'Thomas\\' Birthday',
          start: '2020-01-10',
        },
        {
          name: 'Mash Potatoes',
          start: '2020-01-09 12:30',
          end: '2020-01-09 15:30',
        },
      ],
    }),
    mounted () {
      this.$refs.calendar.scrollToTime('08:00')
    },
  }`,
        today: "2021-06-21",
        events: [
          {
            name: "10 Pedidos",
            start: "2021-06-22 11:15",
            end: "2021-06-22 12:30"
          },
          {
            name: "26 Pedidos",
            start: "2021-06-21 11:10",
            end: "2021-06-21 13:30"
          },
          {
            name: "23 Pedidos",
            start: "2021-06-23 11:50",
            end: "2021-06-23 15:30"
          },
          {
            name: "29 Pedidos",
            start: "2021-06-24 11:30",
            end: "2021-06-24 14:35"
          }
        ]
      },

      today: "2020-01-08",
      focus: "",
      type: "month",
      typeToLabel: {
        month: "Month",
        week: "Week",
        day: "Day",
        "4day": "4 Days"
      },
      start: null,
      end: null,
      selectedEvent: {},
      selectedElement: null,
      selectedOpen: false,
      events: [],
      colors: [
        "blue",
        "indigo",
        "deep-purple",
        "cyan",
        "green",
        "orange",
        "grey darken-1"
      ],
      names: [
        "Meeting",
        "Holiday",
        "PTO",
        "Travel",
        "Event",
        "Birthday",
        "Conference",
        "Party"
      ]
    };
  },
  methods: {
    setActiveTab1(event) {
      this.tabIndex = this.setActiveTab(event);
    },
    setActiveTab2(event) {
      this.tabIndex2 = this.setActiveTab(event);
    },
    /**
     * Set current active on click
     * @param event
     */
    setActiveTab(event) {
      // get all tab links
      const tab = event.target.closest('[role="tablist"]');
      const links = tab.querySelectorAll(".nav-link");
      // remove active tab links
      for (let i = 0; i < links.length; i++) {
        links[i].classList.remove("active");
      }

      // set current active tab
      event.target.classList.add("active");

      // set clicked tab index to bootstrap tab
      return parseInt(event.target.getAttribute("data-tab"));
    }
  }
};
</script>
