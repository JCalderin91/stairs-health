<template>
  <div>
    <info />
    <treatment />
    <v-container>
      <v-row>
        <v-col :md="6">
          <details-clinic />
        </v-col>
        <v-col :md="6">
          <right-panel />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import Info from "@/components/InfoClinic";
import Treatment from "@/components/views/your-spot/Treatment";
import DetailsClinic from "@/components/DetailsClinic";
import RightPanel from "@/components/views/your-spot/RightPanel";

export default {
  components: {
    Info,
    Treatment,
    DetailsClinic,
    RightPanel,
  },
};
</script>