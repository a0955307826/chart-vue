<template>
    <div>
        <Pie :data="chartData" :options="chartOptions" />
    </div>
</template>

<script setup>
import { ref } from 'vue';
import { Pie } from 'vue-chartjs';
import { Chart as ChartJS, Title, Tooltip, Legend, ArcElement, CategoryScale } from 'chart.js';

// 註冊所需的 chart.js 插件
ChartJS.register(Title, Tooltip, Legend, ArcElement, CategoryScale);

// 設置圖表數據和選項
const chartData = ref({
    labels: [],
    datasets: [
        {
            label: ['Red', 'Blue', 'Yellow', 'Grey'],
            backgroundColor: ['#FF6384', '#36A2EB', '#FFCE56', '#E0E0E0'],
            data: [20, 30, 50, 80]
        }
    ]
});

const chartOptions = ref({
    responsive: true,
    plugins: {
        legend: { position: 'top' },
        tooltip: {
            callbacks: {
                label: function(context) {
                    return `${context.label}: ${context.raw}`;
                }
            }
        }
    }
});

</script>

<style scoped>
    .submit {
        margin-left: 10px;
    }
</style>