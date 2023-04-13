<template>
    <section class="studetns-view">
        <div class="container">
            <h5 class="page-title">Список заявлений</h5>
            <studentsTable/>
        </div>
    </section>
</template>

<script>
import studentsTable from '@/features/students/students-table.vue';
export default {
    name: 'StudentsView',
    components: {
        studentsTable
    }
}
</script>

<style  scoped>
.studetns-view {
    min-height: 100vh;
    background-color: var(--blue-super-light);
}

.page-title {
    font-size: var(--font-size-1);
    font-weight: bold;
    padding-top: 48px;
}
</style>