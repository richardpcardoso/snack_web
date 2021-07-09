<template>
  <div class="aside aside-left d-flex flex-column" id="kt_aside" ref="kt_aside">
    <!--begin::Brand-->
    <div
      class="aside-brand d-flex flex-column align-items-center flex-column-auto pt-5 pt-lg-18 pb-10"
    >
      <!--begin::Logo-->
      <div
        class="btn p-0 symbol symbol-60 symbol-light-primary"
        id="kt_quick_user_toggle"
      >
        <router-link to="/">
          <div class="symbol-label">
            <inline-svg
              alt="Logo"
              src="media/svg/avatars/001-boy.svg"
              class="h-75 align-self-end"
            />
          </div>
        </router-link>
      </div>
      <!--end::Logo-->
    </div>
    <!--end::Brand-->
    <!--begin::Nav Wrapper-->
    <div
      class="aside-nav d-flex flex-column align-items-center flex-column-fluid pb-10"
    >
      <!--begin::Nav-->
      <ul class="nav flex-column">
        <!--begin::Item-->
<!--        <li class="nav-item mb-2" v-b-tooltip.hover.right="'Latest Projects'">
          <a
            href="#"
            class="nav-link btn btn-icon btn-hover-text-primary btn-lg active"
          >
            <span class="svg-icon svg-icon-xxl">
              &lt;!&ndash;begin::Svg Icon | path:assets/media/svg/icons/Layout/Layout-4-blocks.svg&ndash;&gt;
              <inline-svg src="media/svg/icons/Layout/Layout-4-blocks.svg" />
              &lt;!&ndash;end::Svg Icon&ndash;&gt;
            </span>
          </a>
        </li>-->
        <!--end::Item-->
      </ul>
      <!--end::Nav-->
    </div>
    <!--end::Nav Wrapper-->
    <!--begin::Footer-->
    <div
      class="aside-footer d-flex flex-column align-items-center flex-column-auto py-8"
    >
      <a
          href="#"
          class="nav-link btn btn-icon btn-hover-text-primary btn-lg"
          data-toggle="tab"
          data-target="#kt_aside_tab_6"
          role="tab"
      >
            <span class="svg-icon svg-icon-xxl">
              <!--begin::Svg Icon | path:assets/media/svg/icons/Files/File-plus.svg-->
              <inline-svg src="media/svg/icons/Home/Door-open.svg" />
              <!--end::Svg Icon-->
            </span>
      </a>
    </div>
    <!--end::Footer-->
  </div>
</template>

<style lang="scss">
/* hide default vue-bootstrap tab links */
.hide-tabs > div:not(.tab-content) {
  display: none;
}
</style>

<script>
import KTLayoutAside from "@/assets/js/layout/base/aside.js";
import KTQuickNotifications from "@/view/layout/extras/offcanvas/QuickNotifications.vue";
import KTQuickActions from "@/view/layout/extras/offcanvas/QuickActions.vue";
import KTQuickPanel from "@/view/layout/extras/offcanvas/QuickPanel.vue";

export default {
  name: "Aside",
  components: {
    KTQuickNotifications,
    KTQuickActions,
    KTQuickPanel
  },
  mounted() {
    this.$nextTick(() => {
      // Init Aside
      KTLayoutAside.init(this.$refs["kt_aside"]);
    });
  }
};
</script>
