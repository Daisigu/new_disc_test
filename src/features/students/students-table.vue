<template>
    <div>
        <searchBar v-model="searchText" />
        <div class="table-container">
            <table v-if="filteredStudents.length">
                <thead>
                    <tr>
                        <th>ФИО</th>
                        <th>Дата подачи заявления</th>
                        <th>Балл по русскому языку</th>
                        <th>Балл по математике</th>
                        <th>Балл по информатике</th>
                        <th>Суммарный балл</th>
                        <th>Процент</th>
                    </tr>
                </thead>
                <tbody>

                    <tr v-for="student in filteredStudents" :key="student.id">
                        <td>{{ student.name }}</td>
                        <td>{{ student.date }}</td>
                        <td :style="{ color: getScoreColor(subject.score) }" v-for="subject in student.subjects">
                            {{ subject.score }}
                        </td>
                        <td :style="{ color: getScoreSumColor(student.subjects) }">{{
                            getScoreSum(student.subjects) }}
                        </td>
                        <td>
                            <circlePercentBar :color="getScoreSumColor(student.subjects)"
                                :percent="getScorePercent(student.subjects)">
                            </circlePercentBar>
                        </td>
                    </tr>

                </tbody>
            </table>
            <p v-if="filteredStudents.length == 0" class="empty-data">
                Студенты с таким именем не найдены
            </p>
        </div>

    </div>
</template>

<script>
import searchBar from '@/features/students/search-bar.vue';
import circlePercentBar from '@/shared/components/UI/circle-percent-bar.vue'
export default {
    components: {
        searchBar, circlePercentBar
    },
    data() {
        return {
            students: [{
                "id": 1,
                "name": "Соколова София Михайловна",
                "date": "2023-01-25",
                "subjects": [{
                    "subject": "Русский язык",
                    "score": "4.3"
                },
                {
                    "subject": "Математика",
                    "score": "2"
                },
                {
                    "subject": "Информатика",
                    "score": "2"
                }
                ]
            },
            {
                "id": 2,
                "name": "Павлов Владислав Эминович",
                "date": "2023-02-24",
                "subjects": [{
                    "subject": "Русский язык",
                    "score": "5"
                },
                {
                    "subject": "Математика",
                    "score": "4"
                },
                {
                    "subject": "Информатика",
                    "score": "5"
                }
                ]
            },
            {
                "id": 3,
                "name": "Филиппов Семён Глебович",
                "date": "2023-01-22",
                "subjects": [{
                    "subject": "Русский язык",
                    "score": "4"
                },
                {
                    "subject": "Математика",
                    "score": "3"
                },
                {
                    "subject": "Информатика",
                    "score": "5"
                }
                ]
            },
            {
                "id": 4,
                "name": "Щукина Мария Викторовна",
                "date": "2023-03-20",
                "subjects": [{
                    "subject": "Русский язык",
                    "score": "4.2"
                },
                {
                    "subject": "Математика",
                    "score": "4.5"
                },
                {
                    "subject": "Информатика",
                    "score": "4.5"
                }
                ]
            },
            {
                "id": 5,
                "name": "Потапова Вера Михайловна",
                "date": "2023-01-21",
                "subjects": [{
                    "subject": "Русский язык",
                    "score": "3"
                },
                {
                    "subject": "Математика",
                    "score": "5"
                },
                {
                    "subject": "Информатика",
                    "score": "4"
                }
                ]
            },
            {
                "id": 6,
                "name": "Ефремова Стефания Максимовна",
                "date": "2023-02-02",
                "subjects": [{
                    "subject": "Русский язык",
                    "score": "4"
                },
                {
                    "subject": "Математика",
                    "score": "4"
                },
                {
                    "subject": "Информатика",
                    "score": "3"
                }
                ]
            },
            {
                "id": 7,
                "name": "Сычев Василий Михайлович",
                "date": "2023-02-02",
                "subjects": [{
                    "subject": "Русский язык",
                    "score": "4.3"
                },
                {
                    "subject": "Математика",
                    "score": "4.8"
                },
                {
                    "subject": "Информатика",
                    "score": "5"
                }
                ]
            },
            {
                "id": 8,
                "name": "Соколова Полина Арсентьевна",
                "date": "2023-01-29",
                "subjects": [{
                    "subject": "Русский язык",
                    "score": "4"
                },
                {
                    "subject": "Математика",
                    "score": "3"
                },
                {
                    "subject": "Информатика",
                    "score": "3"
                }
                ]
            },
            {
                "id": 9,
                "name": "Шаповалов Артемий Сергеевич",
                "date": "2023-01-20",
                "subjects": [{
                    "subject": "Русский язык",
                    "score": "5"
                },
                {
                    "subject": "Математика",
                    "score": "5"
                },
                {
                    "subject": "Информатика",
                    "score": "5"
                }
                ]
            },
            {
                "id": 10,
                "name": "Александрова Милана Тимуровна",
                "date": "2023-01-31",
                "subjects": [{
                    "subject": "Русский язык",
                    "score": "4.5"
                },
                {
                    "subject": "Математика",
                    "score": "3"
                },
                {
                    "subject": "Информатика",
                    "score": "3"
                }
                ]
            }
            ],
            searchText: '',
        }
    },
    methods: {
        getScoreColor(score) {
            if (score >= 4 && score <= 5) {
                return 'var(--green)';
            } else if (score >= 3 && score < 4) {
                return 'var(--orange)';
            } else if (score >= 2 && score < 3) {
                return 'var(--red)';
            }
        },
        getScoreSum(subjects) {
            return subjects.reduce((acc, subject) => acc + parseFloat(subject.score), 0);
        },
        getScorePercent(subjects) {
            let totalScore = this.getScoreSum(subjects);
            return ((totalScore / (subjects.length * 5)) * 100).toFixed(0);
        },
        getScoreSumColor(subjects) {
            const percentage = this.getScorePercent(subjects);
            let color;
            if (percentage >= 90) {
                color = "var(--green)";
            } else if (percentage >= 60) {
                color = "var(--orange)";
            } else {
                color = "var(--red)";
            }
            return color;
        }

    },
    computed: {
        filteredStudents() {
            if (this.searchText) {
                return this.students.filter(
                    (item) =>
                        item.name.toLowerCase().includes(this.searchText.toLowerCase())
                );
            }
            return this.students;
        }
    }
}
</script>

<style scoped>
.table-container {
    margin-top: 24px;
    min-width: 100%;
    overflow-x: auto;
}

thead {
    background-color: transparent;
}

table {
    min-width: 1280px;
    width: 100%;
    border-spacing: 0 4px;
    white-space: nowrap;
}

th,
td {
    text-align: start;
    padding: 10px;
    background-color: var(--white);
}

td {
    border-right: 1px solid var(--blue-light);
    font-weight: bold;
}

th {
    background-color: transparent;
    font-size: 12px;
    text-align: center;
    color: var(--blue);
    font-weight: bold;
}

th:nth-child(1) {
    text-align: start;
}

th:nth-child(1),
td:nth-child(1) {
    width: 40%;
}

th:nth-child(7),
td:nth-child(7) {
    width: 5%;
    text-align: center;
}

.empty-data {
    width: 100%;
    min-height: 300px;
    text-align: center;
    margin-top: 5rem;
}
</style>