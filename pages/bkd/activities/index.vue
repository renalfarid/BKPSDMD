<template>
  <div>
    <div class="container">
      <div class="title">Daftar Kegiatan</div>

      <a-table :columns="columns" :dataSource="data" :scroll="{ x: 980 }">
        <span slot="status" slot-scope="text, record">
          <span v-if="record.status === 'Progress'">
            <a-badge status="processing" :text="record.status" />
          </span>
          <span v-if="record.status === 'Finish'">
            <a-badge status="success" :text="record.status" />
          </span>
        </span>

        <span slot="action" slot-scope="text, record">
          <span v-if="record.status === 'Progress'">
            <nuxt-link to="/bkd/activities/rundown">Rundown</nuxt-link>
            <a-divider type="vertical"></a-divider>
            <nuxt-link to="/bkd/activities/formulir">Formulir</nuxt-link>
          </span>
          <span v-if="record.status === 'Finish'">
            <nuxt-link to="/bkd/activities/rundown">Rundown</nuxt-link>
            <a-divider type="vertical"></a-divider>
            <nuxt-link to="/bkd/activities/detail">Detail</nuxt-link>
          </span>
        </span>
      </a-table>
    </div>
  </div>
</template>
<script>
const columns = [
  {
    title: "Jenis Kegiatan",
    dataIndex: "name",
    key: "name"
  },
  { title: "Peserta", dataIndex: "member", key: "member" },
  { title: "Tanggal Mulai", dataIndex: "startDate", key: "startDate" },
  { title: "Tanggal Berakhir", dataIndex: "endDate", key: "endDate" },
  {
    title: "Status Kegiatan",
    width: 160,
    key: "status",
    scopedSlots: { customRender: "status" }
  },
  {
    title: "Action",
    fixed: "right",
    width: 170,
    scopedSlots: { customRender: "action" }
  }
];

const data = [
  {
    key: "1",
    name: "Diklat Prajabatan Golongan I Angkatan X dan XI Tahun 2019",
    startDate: "Senin, 10 November 2019",
    endDate: "Senin, 1 November 2019",
    member: "40",
    status: "Progress"
  },
  {
    key: "2",
    name: "Diklat Prajabatan Golongan II Angkatan X dan XI Tahun 2019",
    startDate: "Minggu, 17 November 2019",
    endDate: "Senin, 2 November 2019",
    member: "45",
    status: "Finish"
  }
];

export default {
  name: "activities",
  head() {
    return {
      title: "Daftar Kegiatan - BKD"
    };
  },
  data() {
    return {
      data,
      columns
    };
  }
};
</script>