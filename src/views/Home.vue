<template>
  <div class="home">
    <h2>50天範圍內的k線圖</h2>
    <Chart :option="option" style="height:400px" />
    <!-- <button @click="getSocketData">測試</button> -->
  </div>
</template>

<script>
import Chart from "../components/Chart";
export default {
  name: "Home",
  data() {
    return {
      option: {
        // 配置X轴
        xAxis: {
          type: "category",
          data: [],
        },
        // 配置Y轴
        yAxis: {
          scale: true,
          min: 0,
          max: 100,
        },
        series: [
          // K線圖
          {
            type: "candlestick",
            // 元素顯示樣式
            itemStyle: {
              normal: {
                // red
                color: "#ED1C24",
                borderColor: "#ED1C24",
                // green
                color0: "#008000",
                borderColor0: "#008000",
              },
            },
            // K線圖數據
            data: [],
          },
        ],
      },
    };
  },
  created() {
    // 在創建vue實例時連結websocket
    console.log(process.env.VUE_APP_URL);
    // this.webSocket();
  },
  methods: {
    // webSocket() {
    //   console.log(process.env.WEBSOCKET_URL);
    //   const self = this;
    //   if (typeof WebSocket == "undefined") {
    //     this.$notify({
    //       title: "提示",
    //       message: "當前瀏覽器無法接收socket消息，請使用Google Chrome",
    //       type: "warning",
    //       duration: 0,
    //     });
    //   } else {
    //     //socket url and connet
    //     const socketUrl = process.env.WEBSOCKET_URL;
    //     const socket = new WebSocket(socketUrl);
    //     //open socket
    //     socket.onopen = function() {
    //       console.log("瀏覽器WebSocket已開啟");
    //     };
    //     // listen on socket message
    //     socket.onmessage = function(msg) {
    //       // transform message to json format
    //       const data = JSON.parse(msg.data);
    //       const dataDate = data.date;
    //       //限定顯示資料總數（目前為50筆），超過的話就移除首項、push新data到末項
    //       if (self.option.xAxis.data.length >= 50) {
    //         setTimeout(() => {
    //           self.option.xAxis.data.shift();
    //           self.option.series[0].data.shift();
    //         }, 0);
    //         self.option.xAxis.data.push(dataDate);
    //         self.option.series[0].data.push([
    //           data.open,
    //           data.close,
    //           data.low,
    //           data.high,
    //         ]);
    //       } else {
    //         self.option.xAxis.data.push(dataDate);
    //         self.option.series[0].data.push([
    //           data.open,
    //           data.close,
    //           data.low,
    //           data.high,
    //         ]);
    //       }
    //     };
    //   }
    // },
  },

  components: {
    Chart,
  },
};
</script>
