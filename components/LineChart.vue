<script>
// lineChart.js
import { Line, mixins } from 'vue-chartjs'
const { reactiveProp } = mixins

export default {
  extends: Line,
  mixins: [reactiveProp],
  props: ['options'],
  mounted () {
    this.gradient = this.$refs.canvas.getContext('2d').createLinearGradient(0, 0, 0, 450)
    this.gradient2 = this.$refs.canvas.getContext('2d').createLinearGradient(0, 0, 0, 450)

    this.gradient.addColorStop(0, 'rgba(248, 107, 79, 0.5)')
    this.gradient.addColorStop(0.5, 'rgba(248, 107, 790, 0.25)');
    this.gradient.addColorStop(1, 'rgba(248, 107, 790, 0)');

    this.gradient2.addColorStop(0, 'rgba(95, 174, 227, 0.9)')
    this.gradient2.addColorStop(0.5, 'rgba(95, 174, 227, 0.25)');
    this.gradient2.addColorStop(1, 'rgba(95, 174, 227, 0)');
    // this.chartData is created in the mixin.
    // If you want to pass options please create a local options object
    // this.renderChart(this.chartData, this.options)
    this.renderChart({
      labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July'],
      datasets: [
        {
          label: 'Data One',
          borderColor: '#FC2525',
          pointBackgroundColor: 'white',
          borderWidth: 1,
          pointBorderColor: 'white',
          backgroundColor: this.gradient,
          data: [40, 39, 10, 40, 39, 80, 40]
        },{
          label: 'Data Two',
          borderColor: '#05CBE1',
          pointBackgroundColor: 'white',
          pointBorderColor: 'white',
          borderWidth: 1,
          backgroundColor: this.gradient2,
          data: [60, 55, 32, 10, 2, 12, 53]
        }
      ]
    }, {responsive: true, maintainAspectRatio: false})
  }
}
</script>