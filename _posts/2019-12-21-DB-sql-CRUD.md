---
layout: article
title: Database/Data | MariaDB - CRUD 실습해보기
tags: SQL
comments: true

---

## **Today What I Learend**  



가장 중요한 것을 먼저 익히는 것이 중요한 것 아닐까?
쉬워 보일 수는 있지만 가장 중요한 것!
중요한 것일 수록 어쩌면 쉬울 지도..! 



---
**Today I Learend**
- 예전에 본 생활코딩 CRUD
- Create
- Read
- Update
- Delete



---






----


<div style="width:100%;">
<canvas id="canvas" height="300"></canvas>
</div>

<script>

new Chart(document.getElementById("canvas"), {
    type: 'bar',
    data: {
        labels: ['가가가가가가가가가가가가가가', '나나나나나나', '다다다다다다', '라라라라라라', '마마마', '바바바바바바바', '사사사사사사사사', '아아아아아아', '자자자자', '차차차차차차차', '카카카카카카카'],
        datasets: [{
            label: '테스트 데이터셋',
            data: [
                10,
                3,
                30,
                23,
                10,
                5,
                15,
                20,
                13,
                5,
                9
            ],
            borderColor: "rgba(255, 201, 14, 1)",
            backgroundColor: "rgba(255, 201, 14, 0.5)",
            fill: false,
        }]
    },
    options: {
        responsive: true,
        title: {
            display: true,
            text: '막대 차트 테스트'
        },
        tooltips: {
            mode: 'index',
            intersect: false,
            callbacks: {
                title: function(tooltipItems, data) {
                    return data.labels[tooltipItems[0].datasetIndex];
                }
            }
        },
        hover: {
            mode: 'nearest',
            intersect: true
        },
        scales: {
            xAxes: [{
                display: true,
                scaleLabel: {
                    display: true,
                    labelString: 'x축'
                },
                ticks: {
                    autoSkip: false,
                    callback: function(value, index, values) {
                        if (value.length > 8)
                          return value.substr(0, 5) + "...";
                        else
                          return value;
                    }
                }
            }],
            yAxes: [{
                display: true,
                ticks: {
                    suggestedMin: 0,
                },
                scaleLabel: {
                    display: true,
                    labelString: 'y축'
                }
            }]
        }
    }
});

</script>



